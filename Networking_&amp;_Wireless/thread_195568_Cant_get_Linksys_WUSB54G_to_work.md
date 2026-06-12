---
title: "Cant get Linksys WUSB54G to work"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by inuyasharox4776 on 2006-06-13
Ive tried many things here, but all have failed so far. I dont think I have even gotten the ndiswrapper installed yet. Is there an easy guide to get this working?also, would upgrading to 6.06 make installing it a bit easier?

---

### Post by inuyasharox4776 on 2006-06-13
bump. I really want to get this working, so I could copnfigure all my linux stuff from my Ubuntu desktop, instead of going to my Windows partition. What do I need to get it working?

---

### Post by inuyasharox4776 on 2006-06-14
i noticed that when Ubuntu starts up my internet adapter loses power or something, because the lights on it turn off. The adapter isnt even being recognized in Networks:-x all the guides ive seen so far is to get the internet running, and it doesnt even seem im at that level yet. Any help?

---

### Post by inuyasharox4776 on 2006-06-14
since my wireless adapter doesnt seem to start up while its loading in Ubutu, i tried to disconnect it before logging on. but when ubuntu was loading it went into the terminal and gave me this message :
```
* Starting hotplug system...   t system... ring bad line st [ok]
```
i also got some messages about the blacklist, but i didnt have enough room to put this on my arm :p (another question, how do I copy and paste what is in the terminal here?)

---

### Post by inuyasharox4776 on 2006-06-15
ok, i solved that blacklist problem, but now I have another one. If I try to disconnect the adapter and boot up, it stops at "Starting hotplug subsystem" and hangs right there. just for some info, Im running a HP Pavilion a1250n with ATI Radeon X700 Pro graphics card. I tried ctrl+c to skip it, but it does nothing.

---

### Post by inuyasharox4776 on 2006-06-15
ok, i fixed that hotplug problem, and now my wireless card is on. But it is still not showing up in Networking and ifconfig. I also when installing Breezy was not able to configure it, so how would I be able to do that now?

---

### Post by wieman01 on 2006-06-16
Hello, 

Have you followed these instructions?

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

Pretty useful link when it comes to using ndiswrapper with WEP (or even without). 

Copy & paste in a terminal... highlight the text you want to copy (e.g. in your browser) and press crtl+C. Then press the scroll-wheel button while moving the mouse pointer over the terminal windows into which you want to copy the stuff. Works the other way around as well.

---

### Post by inuyasharox4776 on 2006-06-16
[QUOTE=wieman01]Hello, 

Have you followed these instructions?

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

Pretty useful link when it comes to using ndiswrapper with WEP (or even without). 

Copy & paste in a terminal... highlight the text you want to copy (e.g. in your browser) and press crtl+C. Then press the scroll-wheel button while moving the mouse pointer over the terminal windows into which you want to copy the stuff. Works the other way around as well.

He[/QUOTE]
the drivers are already installed for it, but its just not recognizing the WUSB54G

---

### Post by wieman01 on 2006-06-16
Hello again, 

Can you possibly post the content of "/etc/network/interface"? This may help me understand if the settings are incorrect.

P.S.: Ah, and perhaps the "dmesg" output would be nice as well ("sudo dmesg >> myoutput.txt").

---

### Post by inuyasharox4776 on 2006-06-16
ill do my best, but as I am posting from my Windows partition, it may not be perfect. ill try my best htough. just give me a few minutes.

---

### Post by inuyasharox4776 on 2006-06-16
ok, i checked the files, and it was wierd. The interface file was empty and it didnt seem like i could access the dmesg file. Is this normal? ill try again and see if it was a fluke on my part.

---

### Post by inuyasharox4776 on 2006-06-16
ok, ya, it was a fluke. you got to bear with me, as the only way i was able to get the file was to print them, so im going to post the pictures of the copy. im going to get the scans up tomorrow as im going to bed right now;)

---

### Post by wieman01 on 2006-06-16
Hi, 

Well, mate. I think we are getting one step closer. It's definitely wrong that your 'interface' file is empty as it is the starting point for loading & enabling your network card.

Execute the following command in a terminal: 

sudo gedit /etc/network/interface [then enter your password]

Insert the following text (6 lines including an empty one):

auto lo
iface lo inet loopback

auto rausb0
iface rausb0 inet dhcp
       wireless-essid your_essid

.. and save the file ('rausb0' should be the name of your network interface...).

Now either restart OR enter this command:

sudo /etc/init.d/network start

This should load the file and bring up your network interface. Wait for a little while and your computer should connect to your router via DHCP handshake. If you require WEP encryption or static IP or even WPA, we continue the discussion tomorrow. 

Try to fire up firefox and browse through your favorite sites for a while. You'll enjoy it before we embark on encryption.

N.B.: What I meant with dmesg is not the log-file but executing the command mentioned above and posting the resulting text file ("myoutput.txt"). That's it. But perhaps it is not necessary if this solution works.

---

### Post by inuyasharox4776 on 2006-06-16
ok, ill try that but i noticed something sort of intresting last night. i was going through the device manager and noticed that my WUSB54G is being recognized by the device manager. And the interface file wasnt really empty, i think i just mispelled something. ill get those up plus try that command.

---

### Post by vvlist on 2006-06-16
Try compiling the latest ndiswrapper, it worked for my WUSB54Gv4 after trying many different methods like using the rt2xxx drivers...;)

---

### Post by inuyasharox4776 on 2006-06-16
i dont need to compile the new ndiswrapper, since the drivers for the wusb54g are working. The thing thats happening is the wusb54g isnt being recognized (well, it is, but only in device manager)

---

### Post by wieman01 on 2006-06-17
Does that mean your interface is running then? Can you connect to the internet? If not, this is how my '/etc/network/interfaces' file looks like:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
	address 192.168.168.40
	netmask 255.255.255.0
	gateway 192.168.168.230
	wireless-essid My_Wireless_Network

I am using static IPs for my WUSB54g (also V4). Perhaps you can try this.

---

### Post by inuyasharox4776 on 2006-06-19
ya, i think ill try that. But no, I cant connect to the internet. Its only showing up in device manager, and when i use sudo ndiswrapper -l it only shows that the driver is working, and that no hardware is detected.
edit:
tried it, not much happened.

---

### Post by wieman01 on 2006-06-20
Ok, I think the problem is with your USB device. Everything should work now unless there is an issue with the hardware. 

Can you run the command "dmesg" in a terminal and post the output here? This may help determine whether your hardware has been recognized and is working.

N.B.: 'sudo dmesg >> myoutput.txt' writes the system message into a text file. Post the file in here.

---

### Post by inuyasharox4776 on 2006-06-20
i had to scan them so here they are:
[http://i5.tinypic.com/14y8p3r.jpg](http://i5.tinypic.com/14y8p3r.jpg)
[http://i5.tinypic.com/14y7r68.jpg](http://i5.tinypic.com/14y7r68.jpg)
[http://i6.tinypic.com/14y8z00.jpg](http://i6.tinypic.com/14y8z00.jpg)
[http://i5.tinypic.com/14y9y0w.jpg](http://i5.tinypic.com/14y9y0w.jpg)
this is only some of the files, ill upload the rest tomorrow

---

### Post by inuyasharox4776 on 2006-06-22
sorry i didnt get to post the files today, my day has been sort of traumatic. ill try to get them posted up pretty soon.

---

### Post by xoui on 2006-06-23
[QUOTE=wieman01]Hello again, 

Can you possibly post the content of "/etc/network/interface"? This may help me understand if the settings are incorrect.

He

P.S.: Ah, and perhaps the "dmesg" output would be nice as well ("sudo dmesg >> myoutput.txt").[/QUOTE]

Should be /etc/network/interfaces

---

### Post by wieman01 on 2006-06-24
Hello, 

Well... I don't have to tell you that you don't need to scan anything, do I? A simple command in a terminal will generate a text-file for you that you could post here:

> dmesg >> file.txt

Then open the file and copy & paste the content.

---

### Post by inuyasharox4776 on 2006-06-30
sorry i havent been here for awhile. I cant paste it here since I dont have internet acess in Linux, only my Windows partition, that is why I have to scan it.

---

### Post by inuyasharox4776 on 2006-07-20
once again...im sorry i havent been here. So far, I have almost completely given up on Linux since it is hard to get this working.

---

### Post by inuyasharox4776 on 2006-07-26
ok, I have just recieved my Dapper Drake CDs in the mail right now, and Im thinking of uninstalling Breezy and installing Dapper.

---

### Post by goonies on 2006-08-04
> **vvlist said:**
> Try compiling the latest ndiswrapper, it worked for my WUSB54Gv4 after trying many different methods like using the rt2xxx drivers...;)

have u managed to keep a stable connection? if so how

---

### Post by cantormath on 2006-08-04
>  inuyasharox4776  

Unhappy Cant get Linksys WUSB54G to work
Ive tried many things here, but all have failed so far. I dont think I have even gotten the ndiswrapper installed yet. Is there an easy guide to get this working?also, would upgrading to 6.06 make installing it a bit easier?

I had the same exact problem....

Here is the site with the drivers...
[http://prism54.org/](http://prism54.org/)

Get on freenode on irc,
goto #prism54
talk to redhead or slice.
they will talk you through it.
you need to install the prism54 driver for usb, which is not in the kernel.
it took me a while. 

You might be better off getting another card.

---

### Post by goonies on 2006-08-04
> **cantormath said:**
> I had the same exact problem....

Here is the site with the drivers...
[http://prism54.org/](http://prism54.org/)

Get on freenode on irc,
goto #prism54
talk to redhead or slice.
they will talk you through it.
you need to install the prism54 driver for usb, which is not in the kernel.
it took me a while. 

You might be better off getting another card.

is this for my question?

---

### Post by cantormath on 2006-08-04
> **goonies said:**
> is this for my question?

sorry I changed it.

---

### Post by cantormath on 2006-08-04
> **inuyasharox4776 said:**
> ill do my best, but as I am posting from my Windows partition, it may not be perfect. ill try my best htough. just give me a few minutes.

Here is another way, take a look at this tutorial.
[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

---

