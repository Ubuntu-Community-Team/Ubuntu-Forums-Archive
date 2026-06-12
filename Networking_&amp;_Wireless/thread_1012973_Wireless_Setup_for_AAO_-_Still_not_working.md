---
title: "Wireless Setup for AAO - Still not working"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by stoopid_noob on 2008-12-16
So, I was finally able to reinstall Ubuntu, I figured I would give it a real honest effort before giving up. So here is what I know so far.

I followed all of the steps given here: [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

And still I am not able to get wireless or even wired for that matter. If I connect the AAO via cable it sits there and spins and then finally just says "Disconnected." SWEEET!

I followed all of the steps in the above link but still nothing. 

iwconfig info:

lo     no wireless connections

eth0   no wireless connections

pan0   no wireless connections


If I go to Hardware drivers it states:

"Support for Atheros 802.11 wireless LAN cards" and it has a blue circular arrow next to it. 

Below that it says "Support for Atheros 802.11 wireless LAN cards.
An award symbol "Tested by the Ubuntu developers"
License: Free 

At the bottom the same arrow is there and it says "This drive was just disabled, but is still in use." And the activate button is green meaning I can click it. Nothing happens when I do. 




At this point I REALLY just want to make this damn thing work, I very rarely get frustrated with this sort of thing, and I am quite computer savvy. But this is becoming ridiculous. Are there no step by steps available for this? For people that don't have a college degree in Linux programming? 

Any help here would be greatly appreciated this is going to be my last pitch effort.

---

### Post by neu2buntu on 2008-12-16
you have to use the ath5k drivers ...i will have a look at my set up ,there are quite a few steps to get the wireless working,but i will try my best 4 u

---

### Post by stoopid_noob on 2008-12-16
Thank you, much appreciated.

I really do like what I see so far from the OS. I hate Windows and do not want to go through the trouble of putting OSX on here just yet. But I need wireless for this thing. I will actually die without the internet. 

:p

Thanks again.

---

### Post by neu2buntu on 2008-12-16
your first step is you will need to  install linux-backports-modules-intrepid-generic  ,,.did you open the network-manager(found on the top panel) and try clicking on wired network with aao connected to your modem

---

### Post by stoopid_noob on 2008-12-16
Hi,

Yes, I connected it and the blue thing spins with two green things. :P 

But it doesn't connect at all. It just spins and spins until finally it just quits and says disconnected. 

Any reason why this would happen?

---

### Post by neu2buntu on 2008-12-16
this is it just trying to connect then timing out (i never tried my aao on wired connection but it should work).. ok try right clicking on the network-manager then left click on edit connections ,click on auto eth0 then on edit...make sure you have connect automatically ticked and system setting also                .and in the ip4 window have automatic dhpc too,.  are your settings like this already?

---

### Post by stoopid_noob on 2008-12-16
UPDATE!

I connected the ONE through the router rather right through the modem and the wired connection now works. 

So, in other words I am connected. 

From here I do?

---

### Post by neu2buntu on 2008-12-16
right open the terminal found in applications accesories  and type in the command  Code: sudo apt-get install linux-backports-modules-intrepid-generic.....oh and hit return ant type your password(your password will not show as text,)

---

### Post by stoopid_noob on 2008-12-16
I tried this and it states:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-intrepid-generic

---

### Post by neu2buntu on 2008-12-16
oh yes forgot you will have to enable these sources....click on system-administration-software sources ,then in ubuntu software tick all boxes except cdrom ,(next window)third party software tick all boxes,(next window) updates tick all boxes,this should do it for now .then run the install command again............. this will probably seem like a lot of work but the longer your on ubuntu the easier it gets

---

### Post by stoopid_noob on 2008-12-16
Ok update is done and I rebooted. It looked to install everything. 

I have 202 updates available at this point. Should I do them all?

---

### Post by neu2buntu on 2008-12-16
how are you getting on with it..there are a couple more steps to do and hopefully you will be free of wires...

---

### Post by neu2buntu on 2008-12-16
yeah probably better to,.this will bring you up to date....

---

### Post by neu2buntu on 2008-12-16
next after your update open the terminal again and type command Code: sudo apt-get install madwifi-tools   

then sudo gedit /etc/modprobe.d/blacklist ,this will bring up a text file and scroll to the bottom ,hit enter to leave a line of space and add these next lines:-

# try to get wireless working on acer one
blacklist ath_pci 

then sudo gedit /etc/rc.local ,and add this:-

modprobe ath5k                 (add this directly below the line exit0)

and make sure to press save for both these commands

---

### Post by stoopid_noob on 2008-12-16
Ok, it is installing all of the updates. I will reboot afterwards.

And install the madWIFI-tools

---

### Post by neu2buntu on 2008-12-16
yeah.... and i edited step #14(above) there are 2 more commands(steps) for you to follow...... do these commands before you reboot and when your back up again go to your hardware drivers (system-administration-hardware drivers) and activate support for 5xxx series of atheros and deactivate support for atheros 802.11 wireless..... cant rem if you have to reboot (wont do any harm) and hopefully you will be good to go

---

### Post by stoopid_noob on 2008-12-16
Perfect. All of the above done and restarted. 

Next?

---

### Post by neu2buntu on 2008-12-16
go back up to step #14 i edited it

---

### Post by neu2buntu on 2008-12-16
be carefull here not to delete anything already there and after each edit of the text files make sure to press save (top left)

---

### Post by stoopid_noob on 2008-12-16
Yep, I did that, and when I go into the Hardware Drivers I see:

5xxx driver is already activated
Atheros 802.11 driver is there but not active

Should I just be able to disconnect the hardwire and connect wirelessly??!?!? .... we shall see!

:guitar:

---

### Post by neu2buntu on 2008-12-16
fingers crossed.... i am getting my stepson an aao for xmas so i will have to go through all this too if im to install ubuntu onto it ,just hope i havnt missede anything haha

---

### Post by stoopid_noob on 2008-12-16
UGH! As stated it sees the driver, but it doesn't pick up any networks under the wireless tab. 

Back to square one? Or are there other things we need to do? 

Thanks.

---

### Post by neu2buntu on 2008-12-16
ther might be somewhere else that is blacklisting the ath5k drivers ie they have a # infront of them. i will look into this .it was a few months ago when i did all this ..i will get back with you in a minute ok

---

### Post by stoopid_noob on 2008-12-16
Ok, will do.

Thanks.

---

### Post by neu2buntu on 2008-12-16
2 more things to try just incase 1 pull your wireless switch once to the right( the led wont work ,there is no fix yet) then try a complete shutdown then start up ,just incase...then try to see if your ap can be picked up


i get this prob sometimes when ive accidently moved my wireless led switch and because it doesnt light up i dont know whether its on or not

---

### Post by neu2buntu on 2008-12-16
heres another line i have noticed on my comp...  do code :- sudo gedit /etc/modprobe.d/madwifi   and uncomment ie remove # from these lines :-

blacklist ath_hal
blacklist ath_pci

and save......  how are you getting on ,any joy with wifi?

---

### Post by stoopid_noob on 2008-12-16
Still no dice. :(

I am getting so frustrated. I leave for a business trip in the morning and wanted to take this with me for it, BAHHHHH!!!

I thank you for your efforts, though. Let me know if have any other suggestions, you have helped me more than anyone else here. 

Thanks again,

Christopher

---

### Post by stoopid_noob on 2008-12-16
HOLY CRAP!

I went into the etc/modules/ and added "ath5k" at the bottom. Now under the Connections I see "Wireless Networks" but it doesn't see my network. I tried to add it manually but still no dice. 

Any ideas at this point? I feel like I am soooo close!!!

Please help!

---

### Post by stoopid_noob on 2008-12-16
WOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO!!!!!

:guitar:

I got it! After added that piece, I switched the switch for wireless and rebooted the machine. I then selected "Create Wireless Network" and then added my network. 

Thank you Chrissy you are a life saver!!!

Many thanks. I am going to write a step by step by step by step ... for the Linux idiots like me. :P

I will post it tomorrow. 

Thanks again.

---

### Post by neu2buntu on 2008-12-17
\\:D/glad to be of help, these wee acer aspire ones are a great wee machine!!!   yeah that would be a very usefull post the complete step by step guide....happy ubuntuing.......

---

### Post by cocolocko on 2009-01-24
Hello @ neu2buntu and stoopid_noob,

works also perfectly with my Laptop Acer Aspire 3680 with a Atheros AR242x 802.11abg Wireless PCI Express Adapter, on Kubuntu v8.10 64bit. :mrgreen:

Thanks very much

Greetings

---

### Post by thewizz on 2009-03-16
I have followed everything in this thread (and others) and still can't seem to get my wifi card working.  I am quite new to Linux, but did a little UNIX work a few years ago.  I have an Aspire One and get the same error that started this thread except when I initially look at the hardware drivers, it says "A different version of this driver is in use."  If I try and activate it, I get "This driver was just disabled, but is still in use."  The only thing that seems to work is mobile broadband.  Any help would be appreciated.

---

### Post by neu2buntu on 2009-04-09
> I have followed everything in this thread (and others) and still can't seem to get my wifi card working. I am quite new to Linux, but did a little UNIX work a few years ago. I have an Aspire One and get the same error that started this thread except when I initially look at the hardware drivers, it says "A different version of this driver is in use." If I try and activate it, I get "This driver was just disabled, but is still in use." The only thing that seems to work is mobile broadband. Any help would be appreciated.



are you sure you have blacklisted the other drivers by removing the #? make sure you press save after every file you edit (easy mistake to make).... try going over this post again !!

---

