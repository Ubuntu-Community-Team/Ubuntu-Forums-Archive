---
title: "Wireless disabled"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by Onthebit on 2012-02-10
I am illiterate.  Trying to follow instructions from:  [https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting-hardware-check.html](https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting-hardware-check.html)
When I type in the command:

sudo apt-get install 1shw

I get this:

E: Unable to locate package 1shw

Ubuntu 11.10

Thanks

---

### Post by jerrrys on 2012-02-10
copy and paste to terminal then enter

lshw

---

### Post by Onthebit on 2012-02-10
OK, maybe i am typing a one (1) instead of an l (L)??

---

### Post by Onthebit on 2012-02-10
OMG I was typing 1 instead of l.....Ok bear w me I am new!:popcorn:

---

### Post by jerrrys on 2012-02-10
Yep, copy & paste is the way to go.  Other than see your hardware in terminal, are you trying to accomplish something else?

---

### Post by Miljet on 2012-02-10
For future information, the command "ls" is short for "list."  It is often used as part of other commands.
lshw = list hardware
lspci = list all components connected to PCI bus
lsusb = list all components connected to USB
and so forth

---

### Post by Onthebit on 2012-02-10
Seems my wireless has been disabled?  drivers are there...sigh
Anyone know how to enable it?  I have gone through all the commands from the trouble shooting page now left in the cold again....help?

---

### Post by Onthebit on 2012-02-10
rfkill list all
0:phy0: Wireless Lan
Soft blocked: no
Hard blocked: no

---

### Post by jerrrys on 2012-02-10
Are you running Ubuntu (Unity) 11.10?  What kind of wireless card do you have?  Are you seeing your card with any of the above commands? Is a router involved?  Have you looked here:

[ATTACH]212440[/ATTACH]

---

### Post by Onthebit on 2012-02-10
yes yes

I looked at the 'wireless' and it's blank like your pic.........

---

### Post by Onthebit on 2012-02-10
[IMG]http://i299.photobucket.com/albums/mm308/openbridle/004.jpg[/IMG]


[IMG]http://i299.photobucket.com/albums/mm308/openbridle/001-2.jpg[/IMG]

Thought these images might help...

---

### Post by Onthebit on 2012-02-10
I can connect using the Ethernet cable....

---

### Post by jerrrys on 2012-02-10
Try this:

Create a wireless entry and call it wlan0 (thats a zero) and fill nothing else out.  Then save if it will let you.

[ATTACH]212444[/ATTACH]

I do not run wireless so this is my guess.  Perhaps someone else with wireless experience will step in.  good luck

---

### Post by nothingspecial on 2012-02-10
*Thread moved to **Networking & Wireless**.*

Title changed to reflect the problem.

---

### Post by Onthebit on 2012-02-10
I tried that Jerrrys but it won't let me save....should I be putting in a wep key in the wireless security?

---

### Post by Onthebit on 2012-02-10
> **nothingspecial said:**
> *Thread moved to **Networking & Wireless**.*

Title changed to reflect the problem.

Yes it sure assumes that.....but I don't ;)  but I will learn eventually.  Took me a whole day to find the terminal....then i sat for a day thinking this looks a lot like that scary place called DOS:shock:

OK so I tried assigning SSID thats provided by Bell and went to security typed in the wep key and still nothing................allowed me to save though
:popcorn:

---

### Post by nowifi on 2012-02-10
Greetings,

It may be that Network-Manger needs WiFi turned on - It is the icon in the top right of your screen.

The icons in order on your screen are: an envelope for email, a battery symbol, Network-Manger, volume control for audio and then the time.

Right click the Network-Manager icon (a stylized radio wave beacon) and be sure that both "Enable Networking" and "Enable Wireless" are checked and therefore On.

If wireless is functioning, left clicking that same Network-Manager icon will list the status of your connections as well as available wireless services.

The following command will indicate if your wireless hardware is operating AND connected:

```
[COLOR=Blue]**iwconfig**[/COLOR]
```with output like (colored items will be different and specific to your situation: [COLOR=Red]red[/COLOR] items will be determined by your system's identification and naming conventions while **[COLOR=DarkGreen]green [/COLOR]**are the ambient operating conditions):

```

[COLOR=Red]wlan0[/COLOR]     [COLOR=Red]RT2860[/COLOR] Wireless  ESSID:"[COLOR=Red]whiffle[/COLOR]"  Nickname:"[COLOR=Red]RT2860STA[/COLOR]"
          Mode:Managed  Frequency=**[COLOR=DarkGreen]2.412[/COLOR]** GHz  Access Point: [COLOR=Red]00:00:5A:3D:33:8D[/COLOR]   
          Bit Rate=[COLOR=DarkGreen]**54**[/COLOR] Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=[COLOR=DarkGreen]**100/100**[/COLOR]  Signal level:-[COLOR=DarkGreen]**59**[/COLOR] dBm  Noise level:-**[COLOR=DarkGreen]83[/COLOR]** dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```but if the wireless hardware is on but not connected it will look like:

```

[COLOR=Red]wlan0[/COLOR]     [COLOR=Red]RT2860[/COLOR] Wireless  ESSID:[COLOR=Blue]**""**[/COLOR]  Nickname:"[COLOR=Red]RT2860STA[/COLOR]"
          Mode:Auto  Frequency=**[COLOR=DarkGreen]2.412[/COLOR]** GHz  Access Point: **[COLOR=Blue]Not-Associated[/COLOR]**   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=[COLOR=DarkGreen]**100/100**[/COLOR]  Signal level:-**[COLOR=DarkGreen]49[/COLOR]** dBm  Noise level:-**[COLOR=DarkGreen]115[/COLOR]** dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```and if the wireless is turned totally off (keyboard switch etc.) it will look like:

 ```

[COLOR=Red]wlan0[/COLOR]     [COLOR=Red]RT2860[/COLOR] Wireless  ESSID:[COLOR=Blue]**""**[/COLOR]  Nickname:"[COLOR=Red]RT2860STA[/COLOR]"
          Mode:Auto  Frequency=**[COLOR=DarkGreen]2.412[/COLOR]** GHz  Access Point: Not-Associated   
          Link Quality=[COLOR=DarkGreen]**100/100**[/COLOR]   Signal level:-**[COLOR=DarkGreen]49[/COLOR]** dBm  Noise  level:-**[COLOR=DarkGreen]115[/COLOR]** dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Onthebit on 2012-02-11
UGG!  well at iwconfig it says;
lo     no wireless extensions

eth0   no wireless extensions

wlan0  IEEE 802.11bg ESSID:off/any
       Mode: Managed Access Point: Not-Associated Tx-Power=0 dBm
       Retry long limit:7 RTS thr:off Fragment thr:off
       Power Management: on

---

### Post by Onthebit on 2012-02-11
If I am missing the driver is there a way to update it?  I can access internet through the ethernet cable........:confused:

---

### Post by Miljet on 2012-02-11
I am no expert on wireless problems but here is a link to a thread that apparently solved wireless problems for a lot of people.

[http://ubuntuforums.org/showthread.php?t=1861669&highlight=wireless+internet](http://ubuntuforums.org/showthread.php?t=1861669&highlight=wireless+internet)

Maybe something there will help you.

---

### Post by nowifi on 2012-02-11
Successful activation uses the method [here]("http://ubuntuforums.org/showpost.php?p=11354063&postcount=4") posted by [wildmanne39]("http://ubuntuforums.org/member.php?u=508533"), which is
```

sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install b43-fwcutter firmware-b43-installer
```
as reported for the identical model of wireless Broadcom hardware configuration in this [post]("http://ubuntuforums.org/showpost.php?p=11367690&postcount=31") and [this]("http://ubuntuforums.org/showpost.php?p=11367947&postcount=34") .

-----------------------------------------------------------------------------------------------------------------------------------------
Hardware is definitely there and recognized but ... low level software  is not completing the interfacing - if your machine has a wireless  switch (this can be an actual switch or a Fn key or ... ) be sure that  it is switched [COLOR=Red]**on**[/COLOR], otherwise if it is a  driver issue check the following:

I had (it was stolen) a machine with Broadcom wireless hardware also.

It needed a proprietary driver - there were 2 choices but it was the  second choice which was the correct code (the other was for firmware  extraction).

The drivers could be unloaded (disabled) and the correct one loaded  (enabled) with the ```
**Hardware Drivers**

``` tool in **Administration** (which follows **Preferences**)  in **System**.

(the choices were? **B43** and **B???sta** - my memory fails but  the second choice **B???sta **was definitely the correct one)

It helps to disable Wireless Networking to expedite loading of the  driver but even then on my machine, this driver reloading saturated the  cpu performance at 100% for at least 30 or 40 sec. ... irritating. (The **System  Monitor** tool from the same page can be used to monitor the  operation with the cpu performance graph.)

------------------------------------------------------------------------------------------------------------------------------------
aside:

The repertoire of manually labour intensive software (and its  documentation) that can be brought to bear on these hardware problems  includes but is not limited to:
dmesg
lsmod
lspci
lsusb
lshw
ifconfig
iwconfig
iwlist
modprobe
rfkill
...
and ultimately programming tools such as gcc, c++, etc. to write the  necessary code itself!

Fluency in this environment can be useful but ...
(In order to work, my wireless hardware requires Network Manager to be  preconditioned with ```
sudo iwconfig wlan0 essid <hidden SSID>  key s:<ASCII passcode string>
``` ... groan)
 
A general approach to hardware interfacing is to rely on precedent and  on the automation to do the correct things AUTOMATICALLY! - this is the  21st century AND computers are supposedly built to REDUCE human effort  and NOT make life even more manually labour intensive! (hmmmmm .... oh  well)
 
 Precedent is important so that it is known whether the hardware works or  that in fact it is a well documented bug or failure. It can be an  exceptionally daunting task to determine this from volumes of anecdotal  information or misinformation, particularly if the details are obscure.
 
 If not totally automatic, hopefully the interface activation is just  a click away AND self evident and self directed - ie. icon driven such  as via the **Network Manager** and **Hardware Drivers** tools!

---

