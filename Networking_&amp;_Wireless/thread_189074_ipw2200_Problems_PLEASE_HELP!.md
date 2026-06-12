---
title: "ipw2200 Problems PLEASE HELP!"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by zacharyzelinka on 2006-06-04
I have been having much difficulty configuring my Intel Pro Wireless 2200BG in my HP Pavilion DV1000 (Pentium M 1.6, 512MB, Intel GMA900, 100GB HDD and native Ubuntu 6.06 LTS). The adapter worked in 5.10 but since a clean wipe of the HDD using Webroot System Eraser and a fresh install of 6.06 LTS, the wireless adapter does not work. It will not connect and I cannot even manually turn the adapter on. I have tried all kinds of stuff that has been posted in the forum, but have been unsuccsesful. I wanted to be only using Ubuntu 6.06 LTS, but I cannot use the wireless and I am going to have to go back to XP. I would really like to stay with just Dapper, so any help would be great. I am a newbie to Linux so a guide would be awesome. Thanks and have a great day.

---

### Post by onree on 2006-06-05
Yes, I am having a similar problem -- IPW2200 that was detected and configured perfectly in Breezy but simply won't connect properly in Dapper.  Unlike Breezy, which asked during install about ESSID, WEP key, etc., Dapper just tried to set everything up by itself.  Then, I entered the wireless info through the network configuration tool, and it shows that I've connected -- however, I cannot get an IP address from the router.  Help!

---

### Post by cinephy on 2006-06-05
I'm having some problems here also on my Thinkpad T42. I had the card working for about 3 days and then all of the sudden my wifi light would not come on and I could not connect. The stats in network monitor showed that packets were being sent and recieved but still no connection. I just did a fresh install and once again my card is working. I'm going to log everything that I install and do to see if I can find the cause of this. I did read in the driver README that if you turn the card on then off then on again that it will not work so that may have something to do with it. I'll keep looking into it and hopefully have more info soon. I am at about an intermediate level with linux so no promises that I will figure it out. **crosses fingers**

---

### Post by cinephy on 2006-06-07
Last night was the first night I've tried to use my wireless since the re-install and of course, no dice. The light wouldn't come on and no packets being sent. I had installed wifi-radar earlier that day and tried connecting anyway. Nothing, so I continued with my work. Then, after about 25 minutes, the light popped on and there was some activity. This lasted for about 2 minutes before it cut out and never came back on. Today I got to work and plugged into my network here and low and behold the light came on right away. So now I can only use my wireless when I'm plugged in to a hard-lined network?!? This is starting to wear on my nerves. My /etc/network/interfaces file seems to change about every other reboot - trying to call an eth2 interface sometimes (which is non-existant on my computer) and completely removing eth1, my wireless card. Networking problems seem to be rampant now with Dapper and until they are fixed I may have to try a new OS. I hate to do that because I have really enjoyed this distro, but I cannot accept networking problems and have little time to troubleshoot them.

---

### Post by Bionic_Beefpile on 2006-06-07
I am pretty sure that this issue has to do with the firmware.  To fix it, download the latest firmware from [here]("http://ipw2200.sf.net/firmware.php")

Extract the file
```
tar -xvf ipw2200-fw-3.0
```

change to that directory
```
cd ipw2200-fw-3.0
```

copy all files to firmware directory
```
sudo cp * /lib/firmware
```

Reboot and see if that does it for you.

I did some other things as well, but this was the step that made it work again.

---

### Post by luc1fersflowers on 2006-06-07
Bionic_Beefpile: I did this, is there a way to check to see if it is actualy using the newly installed firmware

---

### Post by Bionic_Beefpile on 2006-06-08
I'm not sure...  Is it working for you now?

The other thing I did (just prior to this) was to install the latest driver from [here]("http://ipw2200.sourceforge.net/").  I'm not sure if it's necessary, because the wireless still didn't work until I upgraded the firmware

If your problem is like mine was originally, if you open a console and do
dmesg | grep ipw

And your firmware isn't loading properly you will see errors there

---

### Post by theine on 2006-06-08
Could you perhaps tell me how you installed the newest driver? If i try to do so, I get loads of errors at compile time, both when compiling ieee80211 and ipw2200.

---

### Post by Bionic_Beefpile on 2006-06-08
I'll try!
I'll start off by saying that I'm running kernel 2.6.16 with the performance patch from this thread:
[http://www.ubuntuforums.org/showthread.php?t=157560](http://www.ubuntuforums.org/showthread.php?t=157560)

Ok, here are the steps that I took to get my wireless working (after the kernel update)
First I installed the ieee80211-1.1.13

It says in the INSTALL file for that one that you need to remove previous versions, but I had a hard time doing that, so I didn't (it takes care of itself, actually)

for this I just did
```

cd /dir/where/you/extracted/tarfile
sudo make
sudo make install
```

It asked some questions about the old version, and whenever I had the chance I told it to remove/replace that version with this one.

IIRC, I had to use sudo even for the make command

Next up was installing the driver (1.1.2), which again pretty much consisted of
```
cd /dir/where/you/extracted/tarfile
sudo make
sudo make install
```

I didn't get any errors with that, but my wireless still wasn't showing up.  It was at this point that I did the firmware steps listed above.

Sorry, it's probably not much help... if you can, post the errors you are getting.

Make sure to do
```
sudo apt-get install build-essential
```

---

### Post by cinephy on 2006-06-08
Firmware upgrade... man I feel extremely dumb now. I upgraded yesterday and my card is working with no issues (so far). Thank you for the insight Bionic_Beefpile. I did not have to install the latest driver - The firmware worked just fine on its own.

---

### Post by theine on 2006-06-08
Thanks a lot for your prompt response. I'll very much appreciate it. I'll try with this new kernel and report back.

---

### Post by Bionic_Beefpile on 2006-06-08
glad to hear it worked (to cinephy)!

I was pretty pissed with Dapper for a day or two.  I was running in to two issues.  The first was that the stock 2.6.15 kernel would freeze at "waiting for root file system", and the older (2.5.12) kernel would boot but I was having this wireless issue.

I think the issue is that the newer kernel looks for the firmware in the wrong spot, so you might even be able to get away with just copying the files over to /lib/firmware, but I figure that as long as you're mucking with it, might as well upgrade as well.

Compiling the kernel and fixing this firmware thing got it all straightened out, and now I'm in love.  I've got Compiz running and it looks amazing.  ::EDIT:: I take it all back... now my [CD drive isn't working]("http://ubuntuforums.org/showthread.php?t=171842") :sigh:

---

### Post by cinephy on 2006-06-08
Just a heads up to anyone who read my last post stating that you ONLY need the firmware. Now in my dmesg I do get a warning.

[INDENT]Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update![/INDENT]

This being said, it probably is best that you do go ahead and upgrade everything. I haven't had a problem yet, but I'm gonna go ahead and take care of this before it becomes one.

---

### Post by rreyes3000 on 2006-06-09
aaargh! wHAT AM i MISSING? I downloaded the firmware as suggested in the first part and can't seem to get past it! I downloaded it to the desktop and whe I go to the bash shell and type "tar . . . " I get a "cannot open: no such file or directory". I am new to changing directories and I am not sure what the problem is. The line in the windows read "rreyes3000@rreyes3000-laptop:~$". The closest experience to command lines I have is DOS.

HELP

---

### Post by mcbane on 2006-06-10
Files on the desktop are in their own directory. Try:

cd Desktop
tar .....
etc.

---

### Post by rreyes3000 on 2006-06-10
I SWARE! I had no idea it was case sensative. Anyway it worked. However, The wifi still does not. I have gone to the Network Settings and see that the wireless connection is Active--all setting are configured as well. Then, I have gone over to the connection properties and changed the connection name over to the wireless (eth1) and the activity and signal strength is strong.

I just cant seem to turn on the wifi switch to enable the connection. There is usually a light that turns on when activated. I know it works because I had gone back to widows then went back to ubuntu. But when I press the button the signal strength in the connection properties drops to zero then back to 100 when on.

Any other suggestions?

---

### Post by Bionic_Beefpile on 2006-06-11
Your light won't necessarily work, it is not always an exact readout of whether or not your wifi is working.  Do you have security enabled on your network?

Put this in your terminal and paste the output here
iwlist scan

---

### Post by rreyes3000 on 2006-06-11
The readout from the terminal is as follows:

rreyes3000@rreyes3000-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:10:8C:78:23
                    ESSID:"rreyes3000"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=93/100  Signal level=-35 dBm
                    Extra: Last beacon: 2990ms ago

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

---

### Post by Bionic_Beefpile on 2006-06-11
Right, so it looks like you are running some sort of security.  You need to make sure your keys are entered correctly

---

### Post by daxia on 2006-06-11
Hi guys,

I'm kind of confused...
What is the difference between the firmware and the driver here with ipw2200?
I thought a firmware is usually referred as the software that is embedded in the device itself, which, in other words, normally needs to be flashed into the device.

So I am assumming the "firmware" we are talking about for ipw2200 is actually the driver? Or else, why do we need two of them?

---

### Post by michaelmastin on 2006-06-18
I know where you are coming from as I was equally confused but the firmware is different.  I just finished compiling the 2.6.16-20 kernel and all I had to do was add the 2.4 firmware to /lib/firmware and it worked, I tried using 3.0 firmware and it would not work.  I was just reading the changes on the new 2.6.17 kernel and it says they just changed it so you must use the 3.0 firmware.  I will find out tonight.  Everything works since I compiled my kernel except my ati card, but that is not as important as my wifi was.

---

