---
title: "Intel Wifi Link 5100 Blinking Light Fixed but need help automating the fix"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by crucialhoax on 2010-02-04
Hello,

I just spent most of my class time in Linux trying to figure out why my Intel wifi card was using the led switch as a activity light. I finally edited the right file and it no longer blinks, it just stays on. However, I have to become root, and type in a command every time I boot up to do resolve the issue. So my question is, can someone please help me write a script to automate the follow commands? If so, that will help a lot of people! :)

The commands that I have to issue every time I sign in to fix the blinking led problem is as follows:

sudo su

echo none >> /sys/bus/pci/drivers/iwlagn/0000:02:00.0/leds/iwl-phy0::assoc/trigger

Now, how do I make a script that will automatically do that for me at start-up?

Any help is greatly apppreciated, honestly :)

Thanks everyone!

---

### Post by kiranmurari on 2010-02-04
> **crucialhoax said:**
> 
echo none >> /sys/bus/pci/drivers/iwlagn/0000:02:00.0/leds/iwl-phy0::assoc/trigger

You can add the command to your /etc/rc.local file
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo none >> /sys/bus/pci/drivers/iwlagn/0000:02:00.0/leds/iwl-phy0::assoc/trigger
exit 0
```Hope this helps.

---

### Post by crucialhoax on 2010-02-04
Im a Linux n00b :popcorn: how would I go about making that file executable? I know I make it in gedit, then what? Sorry for not understanding I'm just trying to learn so I know for future reference. Also, is it possible to write to the file once, and not have a script write to it every boot? Or is this something at the driver level that writes that file over? 

Also, right now I have a script that uses that command but its in /etc/network/if-pre-up.d/iwl-no-blink that script is as follows but does not work:

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then

echo none >> /sys/bus/pci/drivers/iwlagn/0000:02:00.0/leds/iwl-phy0::TX/trigger
  done

echo none >> /sys/bus/pci/drivers/iwlagn/0000:02:00.0/leds/iwl-phy0::RX/trigger
  done

echo none >> /sys/bus/pci/drivers/iwlagn/0000:02:00.0/leds/iwl-phy0::assoc/trigger  
  done

fi



The above script was just made in gedit and placed in that directory, which is probably why it doesn't work. However, will it work in its current directory if its executable?

Thanks so much!! :D

---

### Post by chili555 on 2010-02-04
```
sudo chmod +x /etc/network/if-pre-up.d/iwl-no-blink
``` x is for executable. Is it readable by all and owned by root?```
ls -al /etc/network/if-pre-up.d/iwl-no-blink
```As was said, it can all go in *rc.local*, just as well.

---

### Post by crucialhoax on 2010-02-04
Okay thanks so much. I have another question though. Does this apply system wide? Because there is more than one user on this machine... If it doesn't, how do I apply to both users of the system? Also, I'm assuming there isn't a way to write it only once, and it has to be ran as a script?

Anyways, thanks again. I appreciate all of the help :)

---

### Post by crucialhoax on 2010-02-04
-rwxr-xr-x 1 then it displays my username twice. So it doesn't look like it's owned by root. How do I do that?

Also, I did the recommended above, chmod +x and rebooted the laptop and it still blinks on activity. However if  I were to manually change it, the change applies. Stumped now, there has to be a way to automate that script on bootup for all users because its a real pain. If there is anything I need to do let me know. Thanks.

*edit* I figured out how to change ownership and group, so now the file is -rwxr-xr-x 1 root root when I run ls -al /etc/network/if-pre-up.d/iwl-no-blink so I'm going to reboot and hopefully it works :)

*edit again ha* I rebooted and the script still doesn't work. I have to manually run it.

I just added it to the rc.local file which is owned by root and is set to be executable and it still doesn't stop blinking until I manually do it.

I also found information on how to add the script the the init.d file and make it run at start-up, still did not work. I have no idea now.

---

### Post by crucialhoax on 2010-02-04
I am out of ideas. I put the same script in the init.d directory, made it executable, and changed its ownership to root, and made it run on start-up yet as soon as I sign in it still starts blinking. I have the same script in the if-pre-up.d folder still nothing. This is frustrating...

I just let the laptop sit at the login screen and I didn't login and the behavior is the same. So its not being logged in thats triggering it. So it has to be ran at start-up of the machine or something else because running it once I'm logged in isn't the actual cause. Hmm... Is it possible to make it run as part of the boot process or something so the script is ran before I log in so its done once I am logged in.

Basically there is a file named "trigger" in the directory for the iwlagn led driver. When I run the command of: ```
echo none >> /sys/bus/pci/drivers/iwlagn/0000:02:00.0/leds/iwl-phy0::assoc/trigger
```
it changes the word ```
none
``` in the file already to ```
[none]
``` and the blinking immediately stops. So. The question is, is there a way to save that file with [none] already in it so there is no script involved?
P.S. I tried saving it in gedit and nano and neither will let me write over the file. I believe if the file can be saved with [none] in it then it will work.

I apologize for being so persistent lol. But I'm not the only one with the problem and a lot of the solutions I read didn't work. So once it is worked out it would be nice to share it with everyone with the same problem.

---

### Post by chili555 on 2010-02-04
Instead of adding the whole script to /etc/rc.local, does it work if you simply edit /etc/rc.local to look like:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo none >> /sys/bus/pci/drivers/iwlagn/0000:02:00.0/leds/iwl-phy0::assoc/trigger

echo none >> /sys/bus/pci/drivers/iwlagn/0000:02:00.0/leds/iwl-phy0::TX/trigger

echo none >> /sys/bus/pci/drivers/iwlagn/0000:02:00.0/leds/iwl-phy0::RX/trigger

exit 0
```> Does this apply system wide? It sure should.

---

### Post by crucialhoax on 2010-02-04
I copied and pasted the above and it still does not work. I still have to apply it once I am logged in.

---

### Post by crucialhoax on 2010-02-04
I created a bug for it on the intellinuxwireless.org site. Between there help and this forum I think we can get it :)

---

### Post by crucialhoax on 2010-02-05
Amazing. I tried so many different scripts, searches on this forum and nothing would fix it. So I decided what the heck, I am going to install gnome-network-manager and see what happens... Guess what? It fixed it :) Issue solved. Thanks everyone for their help :KS

---

### Post by crucialhoax on 2010-02-05
I take the above post back. When I resume from sleep the same behavior occurs and I must go into the terminal and input the same commands to make it stop blinking. 

So back to square one...

---

### Post by Ventiman on 2010-10-13
@crucialhoax: what is the current status? Did you manage to fix it?

i work on an Latitude E6410 with Intel Centrino 6300 (3x3 rev35). On lucid, i fixed it using ```
/etc/network/if-up.d/iwl-no-blink
``` with ```
#!/bin/sh

if [ "$IFACE" = "wlan0" ]; then
	for direc in /sys/class/leds/iwl-phy*X
	do
		echo none > $direc/trigger
		# never trigger blinking for TX, RX
	done
	
	for direc in /sys/class/leds/iwl-phy*radio
	do
		echo none > $direc/trigger
		# never trigger blinking for radio
	done

	for direc in /sys/class/leds/iwl-phy0*assoc
	do
		echo phy0assoc > $direc/trigger
		# do trigger blinking during association
	done
fi
```
But upgrading to Maverick broke that fix. I cannot stop my wifi-led from blinking, neither manually nor automated at start-up. 

Anyone any idea?

---

### Post by industry on 2010-10-15
> **kiranmurari said:**
> You can add the command to your /etc/rc.local file
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo none >> /sys/bus/pci/drivers/iwlagn/0000:02:00.0/leds/iwl-phy0::assoc/trigger
exit 0
```Hope this helps.

This worked for me perfectly on 10.04. Thanks so much!.

---

### Post by devter on 2010-11-27
In Maverick not worked for me. Any solutions ?? Thanks.

---

