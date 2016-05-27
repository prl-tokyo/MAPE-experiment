# MAPE-experiment

This repository contains the result of the evaluation of our bidirectional programming-based MAPE-K loop for cloud infrastructures. The raw data, collected from the controller, is available in the `measurements` folder. In the `json` folder are the views sent to the different services during data collection.

## Experimental setup

The evaluation was conducted with each service of the MAPE-K loop running on a different EC2 instance, of type `t2.micro`. The evaluation looked at increasingly large deployments, which were started manually.
For each deployment, the controller was started multiple times, and performance data provided by the controller was collected each time. The actualy deployment or termination of EC2 instances or firewall rules were deactivated, as we are not interested in AWS' performance.

## Replicating the experiment

To replicate the experiment, you will need to run a total of 8 web services: the controller, the monitor, the autoscaling analyser, the autoscaling planner, the firewall analyser and planner (combined in one service), the redundancy analyser and planner (also combined in one service), the executer, and the knowledge base. All services are Spring Boot applications, available from the following repositories:

- [controller service](https://github.com/prl-tokyo/MAPE-controller)
- [monitoring service](https://github.com/prl-tokyo/MAPE-monitoring-service)
- [autoscaling analysis service](https://github.com/prl-tokyo/MAPE-autoscaling-analysis-service)
- [autoscaling planning service](https://github.com/prl-tokyo/MAPE-autoscaling-plan-service)
- [firewall analyser and planner service](https://github.com/prl-tokyo/MAPE-firewall-ap)
- [redundancy analyser and planner service](https://github.com/prl-tokyo/MAPE-redundancy-ap)
- [execution service](https://github.com/prl-tokyo/MAPE-execution-service)
- [knowledge base service](https://github.com/prl-tokyo/MAPE-knowledge-base-service)
 
The knowledge base service will require the [knowledge base bidirectional transformations](https://github.com/prl-tokyo/MAPE-knowledge-base); the executer service will require [Ansible](http://ansible.com/); and the monitoring service will require the AWS Java SDK to be correctly configured.

Configuration details for each service are detailed on their respective homepages.
