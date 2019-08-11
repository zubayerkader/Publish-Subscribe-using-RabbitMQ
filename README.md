# Publish-Subscribe-using-RabbitMQ

﻿Dependencies:   
1. RabbitMQ installation:   
https://www.erlang-solutions.com/resources/download.html#tabs-debian   
https://www.vultr.com/docs/how-to-install-rabbitmq-on-ubuntu-16-04-47    
   
   
1. AMQP-CPP Library: for interaction with rabbitmq   
sudo apt-get install libev-dev -&gt; to install libev for AMQP-CPP   
sudo apt-get install libssl-dev -&gt; to install openssl library for AMQP-CPP   
Read documentation to install and use:   
https://github.com/CopernicaMarketingSoftware/AMQP-CPP    
   
   
1. JSON-CPP Library: for interacting with json   
Installation:   
https://linux.tips/programming/how-to-install-and-use-json-cpp-library-on-ubuntu-linux-os    
Read documentation to use:   
https://github.com/open-source-parsers/jsoncpp    
   
   
1. MongoDB Server:   
https://www.mongodb.com/download-center/community   
   
   
1. MongoDB Terminal Client:   
sudo apt install mongodb-clients   
   
   
1. Mongocxx Driver: for interacting with MongoDB   
Python3 is needed to install libmongoc:   
http://ubuntuhandbook.org/index.php/2017/07/install-python-3-6-1-in-ubuntu-16-04-lts/    
http://mongoc.org/libmongoc/current/installing.html   
http://mongocxx.org/mongocxx-v3/installation/    
   
   
Compile Publisher:   
g++ publisher_demo.cpp -o publish -std=c++11 -lamqpcpp -lpthread -ldl -lev -lssl -ljsoncpp   
Run Publisher:   
./publish 5 mtl_temperature.json mtl_health.json mtl_grade.json mtl_temperature.json mtl_health.json   
   
   
Compile Consumer:   
g++ --std=c++11 consumer_demo.cpp -o consume $(pkg-config --cflags --libs libmongocxx) -Wl,-rpath,/usr/local/lib -lamqpcpp -lpthread -ldl -lev -lssl -ljsoncpp    
Run Consumer   
./consume
