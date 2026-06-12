---
title: "[SOLVED] Internal Wifi Card - Can't Connect to Wifi"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by yarde on 2008-12-10
Hi,

Firstly, hello everyone, i'm a n00b to these forums and a n00b to linux.

Yesterday, i used Wubi to install Ubuntu onto a dual boot format on my laptop. (Asus X50n) And everything was fine apart from connecting to my wifi network. It appears that my wifi isn't working under ubuntu, (as if the drivers aren't installed or something) I have connected to the internet using an ethernet cable. But i still have no look with the wireless, i have tried searching around the internet and various forums, but i'm instantly confused by the "jargan" used.

Thanks in Advance for any help

BTW: this is my wireless card

[IMG]http://i37.tinypic.com/k3t09c.jpg[/IMG]

and this is what happens when i rollover the network manager when wifi switch is at on position

[IMG]http://i38.tinypic.com/33oletu.jpg[/IMG]

---

### Post by acreech on 2008-12-10
This is the same wireless card that I have. 


Go to the link in my signature and try that. It is how I have gotten my wireless card to work.

---

### Post by yarde on 2008-12-10
> **acreech said:**
> This is the same wireless card that I have. 


Go to the link in my signature and try that. It is how I have gotten my wireless card to work.

> **acreech said:**
> I have an Atheros AR5007EG card that I use on a 32 bit system. I have found that the following way is the only way that I can get my card to work. 


```

sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*

wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip

(remove the space between ftp &:, i.e. ftp://)

unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules 

```

restart or reboot the computer after you try these and that is how I get mine to work.

ok, i'm a complete ubuntu noob, so would i have to be connected to the internet for that to work? and could i also just copy and paste that whole code thing into terminal?

---

### Post by acreech on 2008-12-10
> **yarde said:**
> ok, i'm a complete ubuntu noob, so would i have to be connected to the internet for that to work? and could i also just copy and paste that whole code thing into terminal?


Sorry about that. Yes you need to have internet access. I connected by wire to my router and then ran the commands. Each line is a separate command. 

Go to Application>Accessories>Terminal

Enter the commands in this order:

```
sudo -s

```

```
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist

```

```
apt-get install ndiswrapper*

```

On this next command after you copy/paste it into the terminal make sure that remove the space between the "ftp" & ":" so that it looks like "ftp://"

```
wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip

```

```
unzip Wireless*

```

```
cd Atheros

```

```
unzip HR*

```

```
ndiswrapper -i net5211.inf

```

```
echo 'ndiswrapper' >> /etc/modules
```


Then restart the computer. It should work after that.

---

### Post by yarde on 2008-12-10
ok, thank you very much, i'll go try that soon, but when you say start each on a new line, do you mean press enter inbetween each? 

thanks

---

### Post by acreech on 2008-12-10
> **yarde said:**
> ok, thank you very much, i'll go try that soon, but when you say start each on a new line, do you mean press enter inbetween each? 

thanks

Yep. Copy one line and then paste it into your terminal. Then hit enter. When it returns to the command prompt 

```
acreech@acreech-laptop:~$ 

```

then paste the next command and hit enter. 

This is the only way I found would make my card work, however I know there is other solutions to this problem using Madwifi. So if this doesn't work, keep searching. 

Hope this does the trick for you.

---

### Post by acreech on 2008-12-10
Just a note about copy/paste

ctrl+c works to copy code out of the forum, but to paste in the terminal you need a shift+ctrl+v

Or you can highlight the code in the forum and then put your cursor in the terminal (in the right place) and then press the scroll button down on your mouse (if it is so equiped). This will paste the highlighted text.

---

### Post by yarde on 2008-12-10
> **acreech said:**
> Yep. Copy one line and then paste it into your terminal. Then hit enter. When it returns to the command prompt 

```
acreech@acreech-laptop:~$ 

```


ok thanks,

but what is that bit of code for?!?! ;p

---

### Post by acreech on 2008-12-10
That is what your prompt should look like. Well something similar. So when it returns to your original prompt, then enter the next command. 

based on your screen name I would guees that yours will look something like:

yarde@yarde-laptop:~$

Just make sure that it has completed the current command and then returned to the prompt before moving onto your next command. 

After you run the first command it should change your prompt to 

root@yarde-laptop:~$

---

### Post by yarde on 2008-12-10
> **acreech said:**
> That is what your prompt should look like. Well something similar. So when it returns to your original prompt, then enter the next command. 

based on your screen name I would guees that yours will look something like:

yarde@yarde-laptop:~$

Just make sure that it has completed the current command and then returned to the prompt before moving onto your next command. 

After you run the first command it should change your prompt to 

root@yarde-laptop:~$

ok, going to try now

brb :p

---

### Post by yarde on 2008-12-10
argh, that didn't work, but i've realised that i didn't have my wifi turned on (theres a switch on the side) during the installation, so i'll try again tomorrow with that on to see if it makes any difference

---

### Post by acreech on 2008-12-10
> **yarde said:**
> argh, that didn't work, but i've realised that i didn't have my wifi turned on (theres a switch on the side) during the installation, so i'll try again tomorrow with that on to see if it makes any difference

Alright. Try again with your wireless switch on. If that does not work then go to post #11 on this thread:

[http://ubuntuforums.org/showthread.php?p=6201697#post6201697]("http://ubuntuforums.org/showthread.php?p=6201697#post6201697")

This is the madwifi method. It also works for some people. 

Also you are going to be asked for the out put of these commands as you reply to other threads to get more technical help than what I can offer. You might put the output here in hopes that someone with more experience than me can help you with the next step.  

```
lspci
```

```
sudo lshw -C network
```

```
sudo ifconfig
```

---

### Post by Swagman on 2008-12-11
Hi Yarde

Any Joy yet ?

---

### Post by yarde on 2008-12-11
> **Swagman said:**
> Hi Yarde

Any Joy yet ?

not had a chance to try the reinstall with the wifi turned on, as i've been at school, but i don't understand the other one that talks about outputs:oops:

---

### Post by Swagman on 2008-12-11
He's talking about the output generated from running the commands he gave you to try

eg: Here is the Output in Terminal after I enter lspci

> 
susan@susans-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
01:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
susan@susans-desktop:~$ 


---

### Post by joshuapbell on 2008-12-11
I figured this out yesterday.

All you have to do is disable your wireless card via the hardware devices under the system>administration>hardware devices

then you install linux-backports-modules-intrepid via synaptic

restart, and it should work

---

### Post by yarde on 2008-12-11
> **joshuapbell said:**
> I figured this out yesterday.

All you have to do is disable your wireless card via the hardware devices under the system>administration>hardware devices

**then you install linux-backports-modules-intrepid via synaptic**

restart, and it should work

ok, but can you provide more specifics about the bit in bold?! cheers

---

### Post by yarde on 2008-12-11
bumpage :p:p:p:p

---

### Post by joshuapbell on 2008-12-11
Go to System>Administration>Synaptic Package Manager

window will popup

in the quick search type backports


look for and install linux-backports-modules-intrepid.

sorry I didn't respond sooner I got kicked out of the house by my wife, she was having a christmas party with a bunch of ladies from church...So I **HAD** to leave

Hope this works for you.

---

### Post by Swagman on 2008-12-11
Mick ..

[img]http://www.upload3r.com/serve/111208/1229052576.jpeg[/img]

---

### Post by joshuapbell on 2008-12-11
Install this package

[IMG]http://www.bhsroe.k12.il.us/bureauvalley/test/screenshot.png[/IMG]

---

### Post by yarde on 2008-12-12
ok, cheers everyone, i'll try that tonight, got to go to school now :p

---

### Post by yarde on 2008-12-12
> **Swagman said:**
> Mick ..

[img]http://www.upload3r.com/serve/111208/1229052576.jpeg[/img]

alright lads and lasses, the task of trying to get this problematic fellow working begins :p

Swagman (or Outcast :p), once i changed them settings, it downloaded 54 updates, now its doing somemore, in fact 202 more !! so lets wait and see what these bring :p

---

### Post by yarde on 2008-12-12
> **joshuapbell said:**
> Install this package

[IMG]http://www.bhsroe.k12.il.us/bureauvalley/test/screenshot.png[/IMG]

IT WORKED

it got a bubble saying wireless networks availible, its still trying to connect, but least i now no that my wifi card is working. :D:D

this there some sort of reputation system on here?

---

### Post by joshuapbell on 2008-12-12
> **yarde said:**
> IT WORKED

it got a bubble saying wireless networks availible, its still trying to connect, but least i now no that my wifi card is working. :D:D

this there some sort of reputation system on here?

You are welcome.

---

### Post by Swagman on 2008-12-12
Excellent job Mick.. 

Can you edit your thread title to say **[SOLVED]** please.


Put Atheros in the title as well and people will be able to track how you succeeded in getting it working.

[edit]

The rep system here is.. Look to the bottom right of each post (not your own) past that arrow thingy.. that is a "Thanks" icon

---

### Post by gnusci on 2008-12-12
I also will like to see Atheros in the OP title, this thread is a great manual.

---

### Post by yarde on 2008-12-13
> **Swagman said:**
> Excellent job Mick.. 

Can you edit your thread title to say **[SOLVED]** please.


Put Atheros in the title as well and people will be able to track how you succeeded in getting it working.

[edit]

The rep system here is.. Look to the bottom right of each post (not your own) past that arrow thingy.. that is a "Thanks" icon

Do i just do what i do on ebuyer? Go advanced > change the title?

**EDIT: Worked out how to do the solved thing**
> **gnusci said:**
> I also will like to see Atheros in the OP title, this thread is a great manual.

how do i edit the title?

thanks again to all that helped

---

### Post by Snappo on 2008-12-13
I have the same card and having been running Ubuntu for a year without use of my internal wifi.

---

### Post by acreech on 2008-12-14
> **yarde said:**
> how do i edit the title?



You can go to your first post and click on edit (lower right hand corner of the post). Then click on "Go Advanced". That will bring up the ability to change the title of the thread. 

Glad you found away to get it to work on your computer. 

acreech

---

### Post by Catsworth on 2008-12-14
Hi Guys,

I've changed the settings for the repositories (in the updates tab shown above) and reloaded everything, but when I search for 'backport' there's nothing in the list.

Any ideas on what's going wrong here?

Thanks :)

---

### Post by joshuapbell on 2008-12-14
> **Catsworth said:**
> Hi Guys,

I've changed the settings for the repositories (in the updates tab shown above) and reloaded everything, but when I search for 'backport' there's nothing in the list.

Any ideas on what's going wrong here?

Thanks :)

Add a 's' to 'backport'.

Also, I don't think I had to change the repos...

---

### Post by yarde on 2008-12-15
> **Catsworth said:**
> Hi Guys,

I've changed the settings for the repositories (in the updates tab shown above) and reloaded everything, but when I search for 'backport' there's nothing in the list.

Any ideas on what's going wrong here?

Thanks :)

have you got it connected to the internet?

you may have to link straigh to your router via ethernet

---

### Post by joshuapbell on 2008-12-15
> **yarde said:**
> have you got it connected to the internet?

you may have to link straigh to your router via ethernet

Oh yeah I forgot to mention that. whoops.

---

### Post by Catsworth on 2008-12-17
Yep, was all connected to the 'net at the time - have a new problem now, the damn Ethernet adaptor's stopped working :(

I'll solve that first and then come back to this one, thanks for the tips though. :)

---

### Post by joshuapbell on 2008-12-17
> **Catsworth said:**
> Yep, was all connected to the 'net at the time - have a new problem now, the *** Ethernet adaptor's stopped working :(

I'll solve that first and then come back to this one, thanks for the tips though. :)

well if the Ethernet adaptor stopped working, then perhaps you weren't connected to the Internet then?

---

