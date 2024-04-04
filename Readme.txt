This is an example that is inspired/modified by the PX4 demo for HITL simulation using a Simulink plant and controller. Refer to the doc: https://www.mathworks.com/help/uav/px4/ref/hitl-simulink-plant-example.html or openExample('px4/PX4HITLSimulationSimulinkPlantExample') to view in MATLAB.

I am logging a new message as at the time, trying to log vehicle_Attitude_setpoint was causing an unreadable error when being logged with a certain set of other topics. The message is titled 'vehAttSet' and will needed to be added to your PX4 source code installation (or the block logging that topic can be removed)

The main difference here is in the controller. I have new PID values that are called from a preload fcn. I have also included an RC Input block, and use 1 channel to toggle between manual/mission mode in the model. This is required as currently, I need to be bother armed & in manual mode because switching to mission in QGC.

The manual mode controller is very primiative/not that easy to control (similar to acro mode). The switch blocks can be connected to the subtract port to 'dampen' velocity when the joystick is centered, acting more as a position mode.