---
title: "Buffalo WLI-UC-GN via Ralink 2870 USB connectivity"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by CB_Rider on 2011-01-09
_I recently upgraded _my Ubuntu edition from Ubuntu 10.04 to 10.10. Everything went smoothly except for one problem: my wireless adapter stopped working properly. What I experienced was that the wireless connection would work for a short (~20-50 seconds) time, then disconnect and not reconnect. I am using a Buffalo WLI-UC-GN USB dongle to connect. It turns out that this adapter uses a Ralink 2870 chip in it. I have spent a lot of time following threads, and fiddling around, but I was not able to get things to work (completely) until now. 

Below is the MOST RECENT thing that I tried that made things work. I have no idea whether this is the only thing that needs done, or if something else that I did before in conjunction with this is required. Please respond if anyone else tries this and is successful or unsuccessful. My success was based on instructions in this thread:

[http://ubuntuforums.org/showthread.php?p=9843048](http://ubuntuforums.org/showthread.php?p=9843048)

Updating the firmware is what fixed things for me. As of today, Ralink provides Linux firmware here:

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

My firmware was the second from the bottom:

Firmware RT28XX/RT30XX USB series (RT2870/RT2770/RT3572/RT3070)

I DL using the link and followed these instructions from the forums:

Go to the directory you downloaded the firmware to earlier; unzip the  firmware archive and go to the directory which (will) house(s) the  firmware.
 	Code:
 	cd firmware_download_dir
unzip RT2870_Firmware*zip
cd RT2870* 
Install the firmware:
 	Code:
 	echo $PWD$(ls *bin) | sed -n 's/^\(.*\)$/sudo mv \"\1\" \"\/lib\/firmware\/\1\" /p' | sh 
Explanation of what the above code does: it lists the firmware (ls  *bin) prepends it to the current working directory ($PWD), feeds that  to the program sed which in turn transforms into a shell command,  finally that is executed.
[SIZE=1]For the curious: sed transforms it to the following shell command (assume that firmware.bin is the name of the firmware): **sudo mv "firmware.bin" "/lib/firmware/firmware.bin"** [SIZE=2][COLOR=Red]**It's a good idea to check that you typed it correctly, you can then execute it safely.**[/COLOR][/SIZE] To do so, merely omit the following bit: | sh. That means to run:  	Code:
 	echo $PWD$(ls *bin) | sed -n 's/^\(.*\)$/sudo mv \"\1\" \"\/lib\/firmware\/\1\" /p' 
 This should output the command mentioned earlier.[/SIZE]

Now everything is working fine. Please, let me know how well this works.

-Lee

---

