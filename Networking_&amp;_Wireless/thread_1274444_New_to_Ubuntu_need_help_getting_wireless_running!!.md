---
title: "New to Ubuntu need help getting wireless running!!"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by frankie31337 on 2009-09-24
Ok im using newest version of ubuntu. My wireless adapter is Us robotics 5426. No linux drivers. I did some reading and found out I should have to use some program called ndisgtk, ndiswrapper-common and ndiswrapper-utils. 
I finally learned how to install those in the terminals. Using what I think was the newest verisons I could find. So it installed correctly and I now had the option of choosing a windows *.inf file for the wireless driver. 
Now first off I would like to say that when I goto the terminal and type lsusb it does NOT show my wireless adapter which is a usb device,. It shows my mouse, my gamepad, my printer but does not show my wireless adapter. Do not know why.
When I uses sudo ndiswrapper -i driver.inf or even when I used the graphical interface from ndisgtk I tried choosing my inf file for my us robotics 5426 driver but it wouldn't work. Believe it told me that it was the incorrect driver or something. I also tried several other drivers for similar us robotics usb wireless devices but they didnt work either. The main inf file I was using was ndisdwm.inf. And in the same directory also was ndiswdm.sys. 
Please any helpm greatly appreciated obviously I will not be able to use ubuntu and learn anything until I can get my wireless adapter working it is frustrating. It even recognizes my pci networkadapter. I know that a big part of the problem must be in the fact that when I type lsusb it lists all my usb devices EXCEPT my usb wireless adapter. Why is this? Please help guys I've been researching and trying different things for 2 days and no luck.
Also I tried [http://www.linuxant.com/driverloader](http://www.linuxant.com/driverloader) which I guess is another way to use windows drivers in linux? I was able to start the install but when it gets to the browser stage and has me log in as root with a password it then tells me it can't download archive.bz2. Not sure why it's tyring to downloadd that since the internet isnt even working yet. Thanks for any help you can also email me at [EMAIL="frankie31337@gmail.com"]frankie31337@gmail.com[/EMAIL] or contact me on xfire at frankie31337.
 
update ; I have since gotten ndiswrapper to accept my driver for my wireless card and it says it is the correct one and even says nthat the hardware is proper or present or something in ndisgtk gui. But when I do lsusb it still does not list my usb wifi adapter and when I click the network manager dealie in the upper left corner it doesnt list any kind of wireless conneciton just has a greyed out wire connection. Ive tried editing the network connecitons and adding the ssid and info for the router but it doesnt even try to conect to it. Theres no wireless options. I dont know if its still not finding my wireless adapter or what the deal is. its a usb us robotics 5426 wireless adapter. Please any help greatly appreciated!

---

### Post by UpsideDownFace on 2009-09-24
When I was having trouble getting my wireless network to work, the thing that did it was changing from Ubuntu 6.06 to Ubuntu 8.04. So having the "latest" isn't always a good thing.

I tried to get ndiswrapper, but found it more complicated than I could understand.
 
When I type "lspci" at a terminal I get a description of the hardware Ubuntu thinks I have - one line is :-

02:2.0 Network cotroller: Intel Corporation PRO/Wireless 2200BG Network connection (rev 05)

 typing "ifconfig" lists lo, eth0, eth1 settings

 typing "iwconfig" shows which of those are wireless connections
 
Under "System > Administration > Network" I have to set up the wireless connection and its properties, including the password for my router.

A program that helps with some wireless networks is "madwifi" which I can get by searching for it under "System > Administration > Synaptic Package Manager", this shows "madwifi tools" as a package that can be downloaded.

Presumably you are using Not-Wireless to get to this forum.

I hope this might give you some clues.

---

### Post by frankie31337 on 2009-10-03
> **UpsideDownFace said:**
> When I was having trouble getting my wireless network to work, the thing that did it was changing from Ubuntu 6.06 to Ubuntu 8.04. So having the "latest" isn't always a good thing.
 
I tried to get ndiswrapper, but found it more complicated than I could understand.
 
When I type "lspci" at a terminal I get a description of the hardware Ubuntu thinks I have - one line is :-
 
02:2.0 Network cotroller: Intel Corporation PRO/Wireless 2200BG Network connection (rev 05)
 
typing "ifconfig" lists lo, eth0, eth1 settings
 
typing "iwconfig" shows which of those are wireless connections
 
Under "System > Administration > Network" I have to set up the wireless connection and its properties, including the password for my router.
 
A program that helps with some wireless networks is "madwifi" which I can get by searching for it under "System > Administration > Synaptic Package Manager", this shows "madwifi tools" as a package that can be downloaded.
 
Presumably you are using Not-Wireless to get to this forum.
 
I hope this might give you some clues.
 
ndiswrapper -l does indeed list that the correct driver is installed! BUT when I do  iwconfig it doesn't show anything.  I don't know what to do next.  When I open the network connections at the top right and goto wireless networks I put in the SSID as 2WIRE767. I enter the correct encryption and password. It has a field for mac address but so far ive left that blank. Anyways it accepts all the info but at the same time never really gives me any option to connect to the wireless network. So im nmot sure whats going on. I think at this point I do have the correct driver installed using ndiswrapper but still cannot figure out how to make it actually connect to the network. Anymore help appreciated man once I can just get freakin linux to connect to the internternet my life and learning linus will be ten times easier cuz right now I have to switch between windows xp and linux when trying to get help.

---

### Post by frankie31337 on 2009-10-04
Need  help from any Linux pros out there. Trying to get wireless internet working on linux so I can stop hopping between xp and linux and focus in linux. Been at this for days now.
 
      Orignally I installed ndiswrapper and the utils.  There are so many different versions I cannot honestly say whether I was using the right ones. I think I found a matching ndiswrapper 1.54 and utils 1.53-1.9..  When I do lsusb it lists my wireless usb as only device 4317:0700 no name or anything.  I copied the inf and sys files for the adapter and installed them using ndiswrapper.  So when I run ndiswrapper -l it does say driver present and then lists the device #. Which made me think I was starting to get it to work.  But when I do iwconfig everything listed all says no wireless extension.  So really not sure whats going on.  I know Im using the correct 32 bit architecture,..  I tried ndiswrapper -v to get the version but I did end up with some error messages and then also at one point someone said do modprobe ndiswrapper which I think also gave me some error messages. Now it was listing the device as working but that got me to thinking that I could have the wrong nidswrapper versions installed? I really don't know any help would be greatly appreciated.

---

### Post by pdc on 2009-10-04
is this it?

[http://www.usr.com/support/product-template.asp?prod=5426](http://www.usr.com/support/product-template.asp?prod=5426)

pretty discouraging that lsusb doesn't show it .........

there are other USB devices: not too expensive; Belkin seem to use ralink that use the rt2870 or rt73 that seem to configure more easily; 

(we were able to configure an rt73 from the ralink readme file as ralink make linux drivers)

[http://ubuntuforums.org/showthread.php?p=8044382#post8044382](http://ubuntuforums.org/showthread.php?p=8044382#post8044382)

sorry I can't offer more specific ndiswrapper advice:

---

### Post by frankie31337 on 2009-10-04
> **pdc said:**
> is this it?
 
[http://www.usr.com/support/product-template.asp?prod=5426](http://www.usr.com/support/product-template.asp?prod=5426)
 
pretty discouraging that lsusb doesn't show it .........
 
there are other USB devices: not too expensive; Belkin seem to use ralink that use the rt2870 or rt73 that seem to configure more easily; 
 
(we were able to configure an rt73 from the ralink readme file as ralink make linux drivers)
 
[http://ubuntuforums.org/showthread.php?p=8044382#post8044382](http://ubuntuforums.org/showthread.php?p=8044382#post8044382)
 
sorry I can't offer more specific ndiswrapper advice:
 
Thats the one. Well lsusb does show it.  It doesn't list it textually like "Us robotics blah blah" but it shows up as Device 4317:0700.  I was lead to believe from someone else that as long as the device ID showed up that it was still recognizing the hardware. And I was even able to install the correct drivers with ndiswrapper but someting must have gone wrong because when I ran iwconfig afterwards it still listed everything as not having a wireless extension.

---

### Post by awam66 on 2009-10-04
Hi,
I suspect this won't be much help, but I have a USRobotics USB wireless adaptor but it is a USR5423 and it works out of the box. No ndiswrapper just native ubuntu. It has worked successfully since hardy heron.

---

### Post by pytheas22 on 2009-10-04
Please post the output of these commands (with the wireless card plugged in):
```

lsmod | grep ndis
sudo modprobe ndiswrapper
uname -rm
dmesg | grep -e ndis -e wlan
ndiswrapper -l
lsusb
lshw -C Network
```

Note that some of the commands may have no output; that's alright.

Since you don't have any Internet connection on Ubuntu right now, the easiest way to post these outputs online would be to copy and paste them into a text file (you can open a text file from Application>Accessories>Text Editor), then transfer the text file to another computer that has Internet access.

---

### Post by frankie31337 on 2009-10-04
> **awam66 said:**
> Hi,
I suspect this won't be much help, but I have a USRobotics USB wireless adaptor but it is a USR5423 and it works out of the box. No ndiswrapper just native ubuntu. It has worked successfully since hardy heron.
 
 
Yeah the easy solution would be to buy a new wireless adapter but I dont have spare money to spend right now.  And now Im determined to make this work one way or another.  I have a 2nd computer running windows XP. I could move my wireless adapter  to that computer if I could get the network running on the comp with ubuntu and figure out how to make it get the network and internet from the XP computer. I have no clue how to do this. Anyone??

---

### Post by frankie31337 on 2009-10-04
> **pytheas22 said:**
> Please post the output of these commands (with the wireless card plugged in):
```

lsmod | grep ndis
sudo modprobe ndiswrapper
uname -rm
dmesg | grep -e ndis -e wlan
ndiswrapper -l
lsusb
lshw -C Network
```
 
Note that some of the commands may have no output; that's alright.
 
Since you don't have any Internet connection on Ubuntu right now, the easiest way to post these outputs online would be to copy and paste them into a text file (you can open a text file from Application>Accessories>Text Editor), then transfer the text file to another computer that has Internet access.
 
Will do and get back to you soon. If I say my files in the *.txt format Linux and Win XP should be able to both read this format right? Im guessing so. Ill figure out how to translate between the two. Thanks for helping so far I'll be back in here when I get a list of those commands copied.
   Also if we find that we can't get the wireless to work I think there is another way that should work 100% if someone can show me how to do it. Let me explain my computer setup right quick.
 
System 1 (best comp) running windows xp with Ubuntu Jaunty installed inside windows. (for now until I get it working then I'll eventually give it a real partition)
 
System 2 running win XP. I could move the wireless adapter to this computer.
 
Since I know for a fact that Ubuntu does recognize my ethernet adapter on sys 1 if I could learn to network Ubuntu sys 1 with Sys 2 running XP with my wireless adapter then I could just get the internet on the ubuntu sys through the lan network.  Lemme know which approach you think would be best.

---

### Post by pytheas22 on 2009-10-04
> If I say my files in the *.txt format Linux and Win XP should be able to both read this format right?

Yes, just save them as plain text files and Windows should open them in Notepad or Wordpad or whatever it uses these days.
> 
Since I know for a fact that Ubuntu does recognize my ethernet adapter on sys 1 if I could learn to network Ubuntu sys 1 with Sys 2 running XP with my wireless adapter then I could just get the internet on the ubuntu sys through the lan network. Lemme know which approach you think would be best.

Something like this should work.  You would need to bridge the wireless and ethernet interfaces together in Windows, and also probably run a dhcp server on the Windows machine.  I don't know enough about Windows networking to know how exactly you would set that up--not sure if Windows can do it on its own or if you'd need third-party add ons--but it seems like it should certainly be possible.

But obviously a better solution would be to make the wireless adapter work in Ubuntu, so let's try that first.

---

