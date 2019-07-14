# ROS Localisation using AMCL
In this project, I used AMCL (Adaptive Monte Carlo Localization) package to localize the Husky robot in a simulated environment.

1. Using a Service called ```/global_localization (std_srvs/Empty)``` provided by the amcl node, all particles are dispersed randomly throughout the free space in the map.
2. After this, the robot then performs a square movement by publishing ```Twist()``` data to ```/cmd_val``` topic.
3. After finishing the movement, it checks particles' covariance.
4.  If this covariance is less than 0.65, this means that the robot has localized itself correctly. Then, the program will end. If this covariance is greater than 0.65, it will repeat the whole the process (disperse the particles, perform the movement, check the covariance...).

To runt the program, first launch the amcl_node:
```roslaunch my_amcl_launcher change_map.launch ```
then launch Rviz:
```rusrun rviz rviz```
and the program file that performs above mentioned steps 1, 2, 3
```roslaunch initialize_particles init_particles_caller.launch```


![Robot Arm](https://i.ibb.co/6Hk5hgG/Screenshot-at-Jul-14-10-28-45.png)
