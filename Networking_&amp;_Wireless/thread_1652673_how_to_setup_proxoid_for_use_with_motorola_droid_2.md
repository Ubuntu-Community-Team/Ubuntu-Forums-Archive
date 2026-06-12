---
title: "how to setup proxoid for use with motorola droid 2.2"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by sevenenemy on 2010-12-25
[http://code.google.com/p/proxoid/wiki/installationLinux](http://code.google.com/p/proxoid/wiki/installationLinux) for starters, have used this link to help set up the phones tethering using wired cable the computer is old with no wireless and it is integrated into the motherboard so dont flame about spending 20 bucks on a wireless card please. i am stuck at 
**Step 3 : Tunneling[¶]("http://code.google.com/p/proxoid/wiki/installationLinux#Step_3_:_Tunneling")**

Now,  we can start tunneling betwwen your computer and your phone. Change  directory to the tools subdirectory of the extracted Android SDK  directory. Issue the command 
./adb forward tcp:8080 tcp:8080

... everything went smooth until here ... there doesnt appear to be a file
named ./adb so i cant move on and dont know where to go from here. 

it is worth noting i am a noob to android sdk and i think i need to set some
more up to get it to work right you download a starter package and the rest 
you reach out and grab with the starter package although i dont know where to
start there either. i am tech savvy just unfamiliar with this sdk any help 
for this christmas disaster would be greatly appreciated. thanks. 

Merry Christmas!

---

### Post by sevenenemy on 2011-02-02
got this working on my own after a lot of searching, using the script found in the link provided, above the video of how to setup the script, [http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html](http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html) is where it is located, and if you read the page setup is a breeze, dont bother messing around with trying to do it yourself, the script does everything for you, and its safe, i have been using it for months now.

---

