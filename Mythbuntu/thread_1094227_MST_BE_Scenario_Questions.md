---
title: "MST B/E Scenario Questions"
date: 2009-03-12
forum: Mythbuntu
---

### Post by rodercot on 2009-03-12
Hey All,

 So I am planning on building another machine for my Master and changing my setup from a master & Slave b/e frontend to One Master and two frontends.

 I have a question about this change. In my setup I have two of the same ExpressVu rcvr's which will each reside on a separate PVR-150 via S-Video inputs and then an OTA antenna connected to a HVR-1250 and finally an FTA connected to another PVR-150. All this is fine. 
 
 What my question is, If I have the same Vu rcvrs on two separate tuners, Is the system going to send the same transmit command to both bell rcvr's at the same time. 

 IE, If I watching LiveTV on one pvr-150 from one rcvr and someone starts to watch live tv on another system from another room in the house, Is the system going to change the channel or disrupt the already playing liveTV session. There is only one channel change script how does it know which rcvr to send commands to at the right time. If both bell rcvr's respond to the same ir commands, when the second livetv session is started and the channel change script sends out the first channel change using the same transmitter and sense both rcvr's respond to the same commands, it will likely change channels on the first rcvr as well I assume. How would I prevent this from being the case.  
 
 I hope this is clear enough. 

 Thanks,

 Dave

---

### Post by newlinux on 2009-03-12
[http://www.mythtv.org/wiki/LIRC#LIRC_with_Multiple_External_Tuners](http://www.mythtv.org/wiki/LIRC#LIRC_with_Multiple_External_Tuners)

might help. I think if they have different lines of sight, you can just use multiple channel change scripts. If they are all the same model, I think you'll have to run multiple LIRC instances, or see if you can set them so they can receive a different set of codes (some STB have this function for when you have multiple in a room or if they have RF support).

---

### Post by abstraktion on 2009-03-12
You should be able to change the ir codes for the receivers to one of 16? codes so that each one will respond to a different set of codes. Then adjust your lirc config with codes for the two receivers independently. Look in the manual for using multiple receivers in the same room. This can be done for nearly all DN receivers and my understanding is that Bev receivers are rebranded DN ones.

Reference:[http://www.mythtv.org/wiki/DISHNetworkLIRCConfiguration]("http://www.mythtv.org/wiki/DISHNetworkLIRCConfiguration")

eric

---

### Post by rodercot on 2009-03-12
Hi Guys,

 Right that makes sense, should had thought about it more. Just change the remote id of one of the rcvrs, I already have the dish config in my lircd file for 1-16 rcvrs. I would still need to have a 2nd channel change script to tell it to use dish1 for example. 

 Dave

---

