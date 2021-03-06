## Output Plugin: Apache Kafka 

Acts as producer to ingest parsed messages to Apache Kafka topics.
This plugin depends on [logagent-output-kakfa](https://www.npmjs.com/package/logagent-output-kafka), which should be installed first. 


### Installation 

Install [@sematext/logagent](https://www.npmjs.com/package/@sematext/logagent) and [logagent-output-kafka](https://www.npmjs.com/package/logagent-output-kafka) npm package: 

```
npm i -g @sematext/logagent 
npm i -g logagent-output-kafka
```
 
### Configuration

```
# Global options
options:
  includeOriginalLine: false

input:
  stdin: true

output:
  kafka: 
   module: logagent-output-kafka
   kafkaHost: localhost
   topic: test
   #Configuration for consider message as  acknowledged acknowledged
   # 0 = No ack required
   # 1 = Leader ack required
   # -1 All in sync replicas ack required
   requireAcks: 1
   sslEnable: false
   #For init sslOptions please refer to to https://nodejs.org/api/tls.html
   sslOptions: 
      - rejectUnauthorized: false

```

### Start logagent

```
logagent --config kafka-input.yaml
```