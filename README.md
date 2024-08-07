## Outcomes
1. Spins up a Flink container
2. Spins up containers supporting OpenLineage: Marquez API, DB, and web
3. Runs a simple [streaming Word Count job](https://github.com/ozzysChiefDataScientist/flink_and_open_lineage/tree/main) that logs an OpenLineage event to Marquez (credit: [Apache Software Foundation](https://github.com/apache/flink/tree/master/flink-examples/flink-examples-streaming/src/main/java/org/apache/flink/streaming/examples/wordcount))

## Prerequisites
1. Download the JAR file used in this example into the root folder
   1. Download pre-compiled jar with `curl https://github.com/ozzysChiefDataScientist/flink_and_open_lineage/blob/main/build/libs/flink_and_open_lineage.jar -o flink_and_open_lineage.jar`
   2. Alteratively, clone [this repo](https://github.com/ozzysChiefDataScientist/flink_and_open_lineage/tree/main) and run `gradle build`

## To Use
1. In terminal, run `docker compose up`
2. Visit [http://localhost:8081/#/overview](http://localhost:8081/#/overview) to see Flink dashboard
3. Visit [http://localhost:3000/](http://localhost:3000/) to see Marquez web UI
4. In a separate terminal tab, run:
   1. `docker cp flink_and_open_lineage.jar jobmanager:/job.jar`
   2. `docker exec -it jobmanager /bin/bash`
   3. Inside the docker container, run `./bin/flink run -c org.gradle.example.simple.WordCount /job.jar`
