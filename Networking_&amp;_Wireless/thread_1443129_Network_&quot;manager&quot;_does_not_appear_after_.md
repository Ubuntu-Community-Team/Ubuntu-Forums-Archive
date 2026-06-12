---
title: "Network &quot;manager&quot; does not appear after installing and uninstalling KWLAN!"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by Alpha517 on 2010-03-30
Hi:
After installing and uninstalling KWLAN and some other network program (I think it was wpa_supplicant GUI) the default Ubuntu network manager does not appear, and I can't connect to ANY form of Internet. PLEASE HELP!!!
Thanks!
PS:I am an UBUNTU NOOB. :KS

---

### Post by ubunterooster on 2010-03-30
Synaptic uninstalled Network manager when you installed KWLAN. Open Synaptic and search for Network Manager.

---

### Post by ubunterooster on 2010-03-30
Proper name I think is: network-manager-gnome. Get this from synaptic.

---

### Post by Alpha517 on 2010-03-30
Hi:
One thing. I can't get internet on the Ubuntu machine. I only have internet on my other computer running XP. Thanks. Anyways, Ubuntu says that network manager is installed even though the icon on the bar up-top is missing. I can't get ANY Internet though. This happened while I was trying to install wpa_supplicant. I installed the two programs I mentioned earlier and then uninstalled them, but network manager is gone, and autoeth0 and wlan1 are not listed anywhere. I also can't install packages from Ubuntu 9.10 CD. I get all sorts of error messages in Terminal. I am willing to reinstall Ubuntu, but GParted doesn't let me delete it's partition. I AM GOING NUTS! PLEASE HELP! lol.:o

---

### Post by ubunterooster on 2010-03-30
No internet. I should have known. Me fEELS Stupid.
   Okay, during a reinstall, can you tell the installer to install to whole disk?

---

### Post by Alpha517 on 2010-03-30
Hehe. Yes, but I really don't want to erase XP. It has all the stuff I use daily. Is there any way to only delete the Ubuntu partition(s)?
Thanks for the help!;)

---

### Post by ubunterooster on 2010-03-30
During the install (at "Prepare disk space") you click "advanced partitions", select the ubuntu partition, say to format it as ext4, and it does not let you do this?

EDIT: You will want to mark the new partition as  "/" [leaving out the quotation marks]

---

### Post by 2hot6ft2 on 2010-03-30
Open a terminal
Applications > Accessories > Terminal
and run

```
gksu gedit /etc/network/interfaces
```
add 2 lines so it looks like this
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
save and close
shut down connect to a wired connection and boot up
then
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install network-manager-gnome
```
When it finishes
```
gksu gedit /etc/network/interfaces
```
remove the 2 lines so it looks like this
> auto lo
iface lo inet loopback
save and close
reboot

---

### Post by Alpha517 on 2010-03-30
Thank you so much! I was just about to maybe quit Linux, and lose a great opportunity. I will try these suggestions, and I will reply. Thanks to all! ;)

---

### Post by Alpha517 on 2010-03-30
IT WORKEEEEEEEEEED!!!!!!! YEEEEEEES!!!!!!!
THANKS!!!!!!!!

One more thing. Can anyone translate this tutorial into simple, plain English for Ubuntu newbies please. I would really appreciate it.

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html:o](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html:o)

---

### Post by Alpha517 on 2010-03-30
In that tutorial it says "comment out" all "lo" entries. It also says create a file called "etc/..." How do I create the file? What does "comment out" mean?, and how do I do it?
Thanks!!!!:)

---

### Post by 2hot6ft2 on 2010-03-30
That is from 2006 don't follow it. Hold on I'll find a decent WPA Supplicant guide

---

### Post by Alpha517 on 2010-03-30
OMG. Thank you soooooooooooooooooooooooooooooooooooo much!:o

---

### Post by ubunterooster on 2010-03-30
Clicking link, I get "page not found" try to fix the link.
Edit: Never mind that, by the time I originally posted this, two posts by you guys negated a need to do such editing.

---

### Post by Alpha517 on 2010-03-30
Here ya go ubunterooster:
[http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html:popcorn:](http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html:popcorn:)

---

### Post by Alpha517 on 2010-03-30
woops it doesnt work hold on

---

### Post by 2hot6ft2 on 2010-03-30
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

And for AES Encryption remove the 2 lines
>        pairwise=CCMP TKIP
       group=CCMP TKIP

That the guide has otherwise you'll get errors running the command in this guide
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

That should help you out.

---

### Post by Alpha517 on 2010-03-30
O I know. Try deleting the :popcorn: and it should work fine.

---

### Post by 2hot6ft2 on 2010-03-30
> **Alpha517 said:**
> Here ya go ubunterooster:
[http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html:popcorn:](http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html:popcorn:)
You keep including the eek and popcorn in the link
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

There you go a link that works

---

### Post by Alpha517 on 2010-03-30
2hot6ft2: What does the guide mean by: your_"psk" Thanks! I mean: what is psk?

---

### Post by 2hot6ft2 on 2010-03-30
> **Alpha517 said:**
> 2hot6ft2: What does the guide mean by: your_"psk" Thanks! I mean: what is psk?
PasSKey
Your passkey

---

### Post by Alpha517 on 2010-03-30
I figured. Hold on, let me try that.

---

### Post by 2hot6ft2 on 2010-03-30
Just so you know. You **can't** use both the interfaces file AND network manager at the same time so if you make changes to the
/etc/network/interfaces file
You'll have either disable or remove network manager
These 2 lines MUST be in the file
> auto lo
iface lo inet loopback
And you can temporarily disable network manager by going to
System > Preferences > Startup Applications
and unchecking it's box
you have to do it more than once for some reason until it stays unchecked.

That way you can test your changes without uninstalling it
Just re-enable it and make the
/etc/network/interfaces file only have these 2 lines and reboot to have Internet again
> auto lo
iface lo inet loopback

---

### Post by Alpha517 on 2010-03-30
Hi:
Can you give me the command to type in Terminal in order to make sure that the lines are there?

---

### Post by 2hot6ft2 on 2010-03-30
> **Alpha517 said:**
> Hi:
Can you give me the command to type in Terminal in order to make sure that the lines are there?
I'm not sure what you mean, what lines are where?

---

### Post by 2hot6ft2 on 2010-03-30
Depends on where you're at in the instructions

---

### Post by Alpha517 on 2010-03-30
Line 5: failed to parse ssid 'linksys'.
Line 5: failed to parse ssid 'linksys'.
Line 12: network block was not terminated properly.
Line 12: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.

I get that. anyways, it is getting late for me, so I will go and be back tomorrow. Thanks. Could you please leave some instructions on how do undo the whole supplicant tutorial? If not, it doesn't matter. Thank you soooooooooo much for all of your help! ;)

---

### Post by Alpha517 on 2010-03-30
Thanks again!!!

---

### Post by 2hot6ft2 on 2010-03-30
I think that the supplicant is only really useful if you're goint to run without a network manager.
Just empty this file and save and close it
```
gksu /etc/wpa_supplicant.conf
```
Getting late here too.
You're welcome.
Tomorrow is another day.

---

### Post by 2hot6ft2 on 2010-03-31
So why are you trying to install kwlan and wpa suplicant?
Does your wifi not work?
If that's the case what wifi adapter do you have?
To find out what it is
Open a terminal
Applications > Accessories > Terminal
and run

If internal PCI
```
lspci
```
That's LSPCI in lower case, and post the results.

If it's a USB adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.

---

### Post by Alpha517 on 2010-03-31
Hi:
No, I am trying to access my wpa protected wifi. My WPC600N linksys card works great. It can connect to unprotected networks under Ubuntu, but not WPA Protected networks. Any help would be greatly appreciated.

---

### Post by 2hot6ft2 on 2010-03-31
Ok, then just follow the guides that I linked to. They're pretty straight forward and easy to follow.

---

### Post by Alpha517 on 2010-04-01
No luck. I followed the instructions and I can't enter my wifi.

---

### Post by worm_java on 2010-04-21
why me not success? i have same problem, after install n uninstalling kwlan, my wireless not detect.. 
i have done in terminal.... sudo apt-get purge CSS apt-get install bliss tuxspace

but an error , coundn't find package CSS.
please help me...:([COLOR=white][SIZE=1]__
[/SIZE][/COLOR]

---

### Post by ubunterooster on 2010-04-21
> **worm_java said:**
> why me not success? i have same problem, after install n uninstalling kwlan, my wireless not detect.. 
i have done in terminal.... sudo apt-get purge CSS apt-get install bliss tuxspace

but an error , coundn't find package CSS.
please help me...:([COLOR=white][SIZE=1]__
[/SIZE][/COLOR]
Dude, I am so sorry. :( My sig is a humourous one not a helpful one. [except for the mark as solved part]

Signatures are not part of the posts.

---

