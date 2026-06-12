---
title: "MCE Tansmitters confused as to where to send commands (fix)"
date: 2009-03-04
forum: Mythbuntu
---

### Post by rodercot on 2009-03-04
Hey All,

 I thought I should post a little workaround that may be helpful, I spent a few days sorting this out. 

 ONE - Remote not responding in LiveTV but the remote still works. Change your playback profile to slim from CPU+ or anything else. My guide would lock up the remote in liveTv for sometimes 15-20 minutes, this change it has been completely solid for a week now.

 TWO - The may not affect everyone but it is useful.
 issue - I have one of the new bell rcvrs that sleep after a certain time frame no matter what you set in the menu, what was happening is after a length of time could be 10 minutes or 10 hours, if there was no activity on the system, the MCE would not transmit upon choosing livetv and obviously with this it would not wake the rcvr up either.

 I had added a couple commands to control my denon rcvr's volume and mute from the mce remote and I added these to lircrc and they call a change_volume.sh script and they transmit on tranmitter 2. **NOTE - I found out via seraching that irexec is called by default in 8.10. You do not have to autostart it. myth looks for any instance of irexec in the lircrc file and if it sees one it loads irexec automagically. These was really confusing at first Because i did not know why I had to instances of irexec running and it was reaking havoc big time.**

 So what I found is whenever I booted the system and I did not touch the vol or mute button on the rcvr myth live tv would transmit as normal. anyhow the fix. 

 Any script I create now that uses the transmitters either one or two. I add irsend SET_TRANSMITTERS 1 or 2 as the first command. So yes I had to modify my channel change script to reflect this as it always sends to transmitter 1 and now all is perfect. after about 3 day of testing. Here is my channel change script below.

 ```
#!/bin/sh
REMOTE_NAME=dish
irsend SET_TRANSMITTERS 1
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select
sleep 0.4
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
sleep 0.5
done
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME select
exit 0 

```  

 THREE - If you have two lirc instances. IE you are using a antec case with the imon ir rcvr and then using a mce to transmit you should create your (any related ir scripts) with the --device= command if you do not they probably will not work correctly and you will get the irsend hardware does not support sending error. 

 this is pretty simple on one of my system I have exactly that. I am using the mce remote (handheld) through the antec imon lcd ir rcvr with lcdproc running and I am using the mce usb dongle to transmit on both tranmitters. I have setup the system to force the modules to load as lirc0 and lirc1 thus this creates sockets lircd and lircd1. my imon is lirc0 and lircd (socket) and my mce dongle is lirc1 and lircd1 (socket). So obviously if I issue a 
 irsend send_once dish 1 2 3 4 as typed I would get a hardware does not support sending error BUT if i issue a 

 irsend --device=/dev/lircd1 send_once dish 1 2 3 4

 VOILA I have transmit functions working. so in your scripts you would run something like.

 #!/bin/bash
 # tell mce which transmitter to use (tell it to use 1 or 2)
 irsend --device=/dev/lircd1 SET_TRANSMITTERS 2
 
 # issue your irsend command for tv power)
 irsend --device=/dev/lircd1 send_once lgtv power

 exit 0.  

 This is a little script you could use to send power to your lgtv to toggle it on or off with a suspend script lets say. you could save it in your scripts dir as power_toggle.sh chmod +x the script and then add it your suspend script by calling it say

 /home/mythtv/scripts/power_toggle.sh before the pm-suspend command of course and it will power off the tv when suspending and if you add it your resume script of course it will power the tv back on. OH and if you only have one lirc instance IE lirc0 and lircd then simply change the device names in the script to lircd instead of lircd1.

 I hope these tips can help some of you. I know! I spent a while getting over some of these issues but they all seem to work quite well now. The WAF factor increases every day.

 Have FUN!!!
  
 rgds,
 
 Dave

---

