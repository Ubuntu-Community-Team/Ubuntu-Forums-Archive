---
title: "Vodafone Mobile Broadband USB stick K3770"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by DesireeMeerkatMaverick on 2011-06-14
My PC crashed and I replaced Windows XP with Ubuntu. My laptop is still on Windows. Haven't been able to connect to the internet on my PC, Linux IT guy told me there was an issue with drivers on Ubuntu. Was told the Ubuntu community would know how to fix this. I've been reading through the posts and found a similar sort of problem posted with a solution posted also. The solution it seemed, lay in the Sakis website. I went to the Sakis website and downloaded  Sakis3G onto my memory stick via my laptop. I need to get internet connectivity on my PC.  My friend advised me to put the stick into the PC and then to  open the terminal and type the following commands: 
gunzip sakis3g.g2 > chmod+xsakis3g > /sakis3g --interactive. Each command on a new line however after typing the first line: gunzip sakis3g.g2, I got 'No such file or directory'.
I'm using Ubuntu 10.10 Maverick Meerkat. 
Any suggestions?

---

### Post by afrodeity on 2011-06-15
> **DesireeMeerkatMaverick said:**
> My PC crashed and I replaced Windows XP with Ubuntu. My laptop is still on Windows. Haven't been able to connect to the internet on my PC, Linux IT guy told me there was an issue with drivers on Ubuntu. Was told the Ubuntu community would know how to fix this. I've been reading through the posts and found a similar sort of problem posted with a solution posted also. The solution it seemed, lay in the Sakis website. I went to the Sakis website and downloaded  Sakis3G onto my memory stick via my laptop. I need to get internet connectivity on my PC.  My friend advised me to put the stick into the PC and then to  open the terminal and type the following commands: 
gunzip sakis3g.g2 > chmod+xsakis3g > /sakis3g --interactive. Each command on a new line however after typing the first line: gunzip sakis3g.g2, I got 'No such file or directory'.
I'm using Ubuntu 10.10 Maverick Meerkat. 
Any suggestions?

Hi Desiree,

Make sure the sakis3g.gz is either in your home directory, something like /home/Desiree/

or on your desktop, something like /home/Desiree/Desktop

You can shorten the command line like this ~/Desktop

when you chmod you need to do this:

```

chmod +x sakis3g

```

---

### Post by DesireeMeerkatMaverick on 2011-06-15
[COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#333333][FONT=lucida grande]This is a continuation of the thread I posted during the early hours of Wednesday morning 14 June 2011: 
[/FONT][/COLOR][/LEFT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#333333][FONT=lucida grande]
[LIST]
[*]
[LIST]
[*]I went back to the literature on the Sakis website. Discovered in my reading that Sakis is only GSM compatible and not CDMA network compatible.  Was advised to try  a ls, which listed the files in the directory in which I found myself.  Important to be in the right directory, for computer programming novices like myself this is a vital bit of information! To change directory : type cd

and cd ..

to go back up a directory.
[*] I'm not sure in which directory I should be?
[/LIST]




[*]
[LIST]
[*]
[/LIST]




[/LIST]
[/FONT][/COLOR][/LEFT][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#333333][FONT=lucida grande]


did the list, yielded a listing of various recognizable folders in blue coloured font, e.g. Adobe Indesign, AOL Saved PFC, Contacts, Desktop, Documents, Downloads. Then white font = 'examples.desktop' yielding again blue fonted folder names e.g. Exchange, Favourites, Music, OpenOffice.org 3.2 (en-US) Installation Files, Pictures, Public, Templates: white fonted heading 'The Church Priest = Aura.pls (this is music, a cd and didn't play on the Amarok nor the other media/music app) with again blue fonted folders e.g. Ubuntu One, (the following two are red-fonted and I recognise they're connected to my current issue) usb-modeswitch_1.1.0-2_i386.deb and usb-modeswitch-data_20100127-1_all.deb; followed by blue fonted folder names e.g. Videos, Windows Software, </end/> When I typed in cd > hit enter > and cd ... The response it gave me :- The programme 'and' is not currently installed. You can install it by typing: sudo apt-get install and[/FONT][/COLOR][/LEFT][/FONT][/COLOR]

---

### Post by DesireeMeerkatMaverick on 2011-06-15
> **afrodeity said:**
> Hi Desiree,

Make sure the sakis3g.gz is either in your home directory, something like /home/Desiree/

or on your desktop, something like /home/Desiree/Desktop

You can shorten the command line like this ~/Desktop

when you chmod you need to do this:

```

chmod +x sakis3g

```


Hi David, please excuse the chaotic manner in which my responses are coming. Figuring my way around the Forum & the rest of it. I guess I should type : ~/Desktop. Having done so I am informed that it's a directory. I guess this is where I type: cd > and cd ... ?  Having done so I'm back to 'No such file or directory. What am I doing incorrectly. Please advise?

---

### Post by afrodeity on 2011-06-15
Question 1: Where did you put the file?

If it is on your desktop do this

```


cd ~/Desktop

ls


```

ls = list

cd = change directory

for basic ubuntu commands look [here]("https://help.ubuntu.com/8.04/basic-commands/C/")

They not that difficult, it is just a case of familiarity. Let me know when you find the file, otherwise try this

```


locate sakis3g


```

PS: If you need to copy a file from your memory stick you can do this

```


cp sakis3g ~/Desktop/


```

make sure you in the directory where you stick is mounted. Something like this /media/<name of stick>

---

### Post by DesireeMeerkatMaverick on 2011-06-15
David, I guess my question should be: what could be the problem if by typing cd I am back to the initial: desiree@desiree-ubuntu:~$

---

### Post by DesireeMeerkatMaverick on 2011-06-15
Excellent! Will go through the commands you gave and familiarize myself. Will post once I've gotten somewhere!

---

### Post by afrodeity on 2011-06-15
> **DesireeMeerkatMaverick said:**
> David, I guess my question should be: what could be the problem if by typing cd I am back to the initial: desiree@desiree-ubuntu:~$

You need to cd into somewhere. If you just cd in your home directory you will get desiree@desiree-ubuntu:~$

if you want to move up a directory you cd ..

(that's two dots)

the furthest you can go is /

which is root

the home directory is this

/home/desiree/

media will be mounted here

/media

Ubuntu follows the Linux file hierarchy. It is quite easy once you know how, but can be a stumbling block until you get a good picture in your head of what the file hierarchy looks like. Most linux systems are the same, completely open source.

---

### Post by DesireeMeerkatMaverick on 2011-06-15
Hey there David, 
Have located the flash stick which was labelled as PRESARIO_RP; I typed in the command lsusb, and it gave me the following list: Bus 004 Device 001: ID 1d6b:001 Linux Foundation 1.1 root hub; the same classification for Bus 003 & Bus 002, with Bus 001 being duplicated as such: 
Bus 001 Device 015: ID 05dc:a781 Lexar Media, Inc. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub.  With my mouse I've selected and copied the above into OpenOffice Writer. I've done this because I'm guessing this is the way to save it to my Desktop? Though I've got a niggling thought telling me that I'm only copying the names listed and not the contents of the device?

Checked properties of doc and saw that it was a 9.998KB size, guessed all had been copied, thus saved it to Desktop.Went to Terminal  and typed locate <name of doc> and everything flashed in perfect display. Now, I've totally forgotten what to do next, going to check our previous notations.

---

### Post by Gregorybekkers on 2011-06-15
Hi,

I've got the same one and use Betavine to let it work.

[http://www.betavine.net/datacards/index.php/Main_Page](http://www.betavine.net/datacards/index.php/Main_Page)

---

### Post by afrodeity on 2011-06-15
> **DesireeMeerkatMaverick said:**
> Hey there David, 
Have located the flash stick which was labelled as PRESARIO_RP; I typed in the command lsusb, and it gave me the following list: Bus 004 Device 001: ID 1d6b:001 Linux Foundation 1.1 root hub; the same classification for Bus 003 & Bus 002, with Bus 001 being duplicated as such: 
Bus 001 Device 015: ID 05dc:a781 Lexar Media, Inc. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub.  With my mouse I've selected and copied the above into OpenOffice Writer. I've done this because I'm guessing this is the way to save it to my Desktop? Though I've got a niggling thought telling me that I'm only copying the names listed and not the contents of the device?

all you need to do is copy the file to your desktop.

```

cd /media

ls

cd PRESARIO_RP

cp sakis3g.gz ~/Desktop

cd ~/Desktop

gunzip sakis3g.gz

chmod +x sakis3g

./sakis3g --interactive



```

Opening it in OpenOffice might damage it, especially if you save it into another format.

However, you might want to try the **betavine** driver first, which is what you were doing before you went off on this mission. Either way, you need to learn some basic skills for using the Terminal programme, so that you can be master/mistress of your own realm. :)

PS: Alternatively try rightclicking on it. Choose Properties. In properties tick executable, then try to double click on file. Choose run.

---

### Post by DesireeMeerkatMaverick on 2011-06-15
Having transferred the doc to my desktop, I tried the first commands you suggested:
 /home/desiree/Desktop/<name of doc>  
note: I'd saved the word doc under a different name and then changed it to Sakis3g from the desktop drop down dialogue box. 
then tried the steps again which yielded the response 'bash:/home/desiree/Desktop/Sakis3g: Permission denied. 
Currently going through the help files on the 'Password and Encryption Keys' window, though I'm wondering whether it might be that I should go to the original file location (~/Documents/Contents copied.odt') and change the name there?

---

### Post by DesireeMeerkatMaverick on 2011-06-15
David, an old habit of mine, going via Cairo to get to Cape Town. Have got the Betavine Page which I'm going through now but I think this is the right one! Thanks for your input!

---

### Post by DesireeMeerkatMaverick on 2011-06-15
GregoryBekkers
Checking out the link you've provided. Reading through the documentation at the moment, looks like it may be just right for me too. Thanks.

---

### Post by afrodeity on 2011-06-15
> **DesireeMeerkatMaverick said:**
> Having transferred the doc to my desktop, I tried the first commands you suggested:
 /home/desiree/Desktop/<name of doc>  
note: I'd saved the word doc under a different name and then changed it to Sakis3g from the desktop drop down dialogue box. 
then tried the steps again which yielded the response 'bash:/home/desiree/Desktop/Sakis3g: Permission denied. 
Currently going through the help files on the 'Password and Encryption Keys' window, though I'm wondering whether it might be that I should go to the original file location (~/Documents/Contents copied.odt') and change the name there?

You need a fresh file, it has nothing to do with doc, or Microsoft, its a packed .gz file which needs to be unpacked in a specific way.

If you need permission to unpack it, then try running the command as root, like this:

```

sudo gunzip sakis3g

```

hopefully gunzip is on your system, you will have to unpack it first, simply changing the name of the file won't help. I see you have a downloaded odt file, which is openoffice, that won't work either, you wanted the .gz file from this [link]("http://www.sakis3g.org/versions/latest/i386/sakis3g.gz") but you were advised to try the betavine driver first from this [link]("http://www.betavine.net/datacards/index.php/Main_Page"), it is probably [ vodafone-mobile-connect_2.25.01-1_all.deb]("https://forge.betavine.net/frs/download.php/626/vodafone-mobile-connect_2.25.01-1_all.deb") and you might need to install [this also]("https://forge.betavine.net/frs/download.php/490/usb-modeswitch_0.9.7_i386.deb"), the usb-mode-switch.

---

### Post by DesireeMeerkatMaverick on 2011-06-15
> **afrodeity said:**
> all you need to do is copy the file to your desktop.

```

cd /media

ls

cd PRESARIO_RP

cp sakis3g.gz ~/Desktop

cd ~/Desktop

gunzip sakis3g.gz

chmod +x sakis3g

./sakis3g --interactive



```

Opening it in OpenOffice might damage it, especially if you save it into another format.

However, you might want to try the **betavine** driver first, which is what you were doing before you went off on this mission. Either way, you need to learn some basic skills for using the Terminal programme, so that you can be master/mistress of your own realm. :)

PS: Alternatively try rightclicking on it. Choose Properties. In properties tick executable, then try to double click on file. Choose run.
Breakthrough ! Realization that the command to list the usb yielded all the usb's . All the input makes a lot more sense to me now. You're absolutely correct about the necessity of familiarizing myself with the Terminal and Commands. The Betavine link provided by GregoryBekkers appears to be the most effective. When I first checked out the Betavine website I didn't go to the Main Page, can't recall which link I used. Nonetheless a learning curve which has certainly enlightened me to a definitive degree though I'm still a far way from being proficient with Ubuntu. Time and patience.

---

### Post by narcisgarcia on 2011-07-01
I'm trying to register this device in usb.ids :

```
12d1  Huawei Technologies Co., Ltd.
    14d1  K3770 USB Modem Stick HSDPA/HSUPA/WCDMA
```

Through [https://usb-ids.gowdy.us/](https://usb-ids.gowdy.us/) and/or [http://www.linux-usb.org/usb-ids.html](http://www.linux-usb.org/usb-ids.html)

I've sent the data by mail, to be included in future *update-usbids* and be listed as something like:
```
12d1:14d1 Huawei Technologies Co., Ltd. K3770 USB Modem Stick HSDPA/HSUPA/WCDMA
```

Note that this device has additional interface for MicroSD memory card, and seems to include some ROM part with Microsoft and Mac drivers.

---

### Post by DesireeMeerkatMaverick on 2011-07-01
Great stuff. Will read through documentation. will post as soon as it's become clear in my head, it's been rather a confusing journey trying to figure out the how to of Ubuntu. 

Appreciate your input.

regards

DesireeMeerkatMaverik

---

### Post by cre8or on 2011-07-02
I got it working after days of painful research
So the solution.
You have to trick linux into thinking it is a different modem, this involves installing usb_modeswitch and editing 3 files
The first file 
**sudo gedit /etc/usb_modeswitch.conf**
add the following lines
DefaultVendor= 0x12d1
DefaultProduct=0x14d1
TargetVendor= 0x12d1
TargetProduct= 0x1c05
CheckSuccess=20
MessageContent="55534243123456780000000000000011060000000000000000000000000000"


The second file you will need to create
**sudo gedit /etc/usb_modeswitch.d/12d1:14d1**

Then add the following lines - yes almost the same as above
################################################## ######
# Huawei K3770

DefaultVendor= 0x12d1
DefaultProduct=0x14d1

TargetVendor= 0x12d1
TargetProduct= 0x1c05
CheckSuccess=20
MessageContent="55534243123456780000000000000011060000000000000000000000000000"

And finally the last file
**sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules**
Add the line


# Huawei Ek3770
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14d1", RUN+="usb_modeswitch '%b/%k'"

I rebooted after this and it works.
I did notice that if you startup with the modem it sometimes does not find it, just pull it out and put it back in.
It works with network manager

---

### Post by DesireeMeerkatMaverick on 2011-07-03
Hello there Cre8or,

I seem to have some sort of issue with my terminal commands, not sure what it is but after typing the first line :  

     sudo gedit/etc/usb_modeswitch.conf 

a request for password follows to which I respond with password, which then yields the following response;

      sudo: gedit/etc/usb_modeswitch.conf : command not found:(

Have checked the help documentation which has informed me of the function of the sudo command. Will seek answer from my help files,  will keep updating status ... 

Thanks for your input  :)
DesireeMeerkatMaverick

---

### Post by cre8or on 2011-07-03
> **DesireeMeerkatMaverick said:**
> Hello there Cre8or,

I seem to have some sort of issue with my terminal commands, not sure what it is but after typing the first line :  

     sudo gedit/etc/usb_modeswitch.conf 

a request for password follows to which I respond with password, which then yields the following response;

      sudo: gedit/etc/usb_modeswitch.conf : command not found:(

Have checked the help documentation which has informed me of the function of the sudo command. Will seek answer from my help files,  will keep updating status ... 

Thanks for your input  :)
DesireeMeerkatMaverick


Hi, you missed a spacebetween gedit and /etc/
sudo gedit/etc/usb_modeswitch.conf 
should be
sudo gedit /etc/usb_modeswitch.conf

however you can use any editing program as long as it has the necessary rights to edit the files, I just prefer to use gedit

---

### Post by cre8or on 2011-07-03
Hi, you missed a spacebetween gedit and /etc/
sudo gedit/etc/usb_modeswitch.conf
should be
sudo gedit /etc/usb_modeswitch.conf

---

### Post by roberthanekom on 2011-07-03
Thank you cre8or! Most progress so far for me.
I seem to hit a wall somewhere. Did you get it working with the Betavine (Vodafone) app or the Sakis 3G app?
When trying the Vodafone app it list nothing under devices.
When trying Sakis 3G:
 - Selecting option "Only switch modem" yields "Modem switched to 12d1:14d1." (I guess this is a good sign.
 - Selecting options "...setup..." , "...prepare..." and "Connect ..." renders error meassages.
Am I missing some steps?

---

### Post by cre8or on 2011-07-04
Hi Robert
I gave up trying to get betavine and Sakis to work and now work it through network manager icon near the time. Give it some time after you plug the modem in. Wait till it starts to flash blue then usually on the third flash you will see it.

---

### Post by roberthanekom on 2011-07-04
Something is still wrong. It never gets to blue. Only a green double-flash every 3 seconds. I tried the whole thing on a laptop with Ubuntu 11.04. Same results.
(I found two things in your coding to be problematic. The space half-way through the MessageContent variable and the lack of a closing " at the end of  ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14d1", RUN+="usb_modeswitch '%b/%k')

What is supposed to set the usb_modeswitch in motion? When I run it from terminal, i.e.:
 [COLOR=Blue]* sudo usb_modeswitch -c /etc/usb_modeswitch.conf*[/COLOR]

I get the following output:

[COLOR=Blue][I]Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 007 on bus 001 ...
Using endpoints 0x0f (out) and 0x8f (in)
Using endpoints 0x0f (out) and 0x8f (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: Vodafone
   Model String: CD ROM (Huawei) 
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI
     Product: Vodafone Mobile Broadband (Huawei)
  Serial No.: not provided
-------------------------
Setting up communication with interface 0 ...
Using endpoint 0x0f for message sending ...
Trying to send message 1 to endpoint 0x0f ...
 OK, message successfully sent
Resetting response endpoint 0x8f
 Error resetting endpoint: -71
Resetting message endpoint 0x0f
 Error resetting endpoint: -19
 Device is gone, skipping any further commands

Checking for mode switch (max. 20 times, once per second) ...
 Original device is gone already, not checking
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Found correct target device

Mode switch succeeded. Bye.[/I][/COLOR]

The stick is still listed as a CD drive under <Places> after the modeswitch.

Any ideas?

---

### Post by cre8or on 2011-07-05
here are the 3 files, just copy them into the right directories.
the work, like I have said, I installed the solution of 3 different machines and different versions of ubuntu.
rename 12d114d1 to 12d1:14d1

Maybe the issue of not getting to blue is the pin.
Do you have a pin code enabled? Have you setup your profile in network manager?

---

### Post by cre8or on 2011-07-05
The above solution works - just installed it on my machine that I reinstalled today.
If the 3 files above do not work then I am not sure what else to do to help you out

Here are the instructions for Network Manager

Screenshots 1-7 Setup Network Manager
Screenshots 8-10 Edit Network Manager for the pin

---

### Post by roberthanekom on 2011-07-05
Its working now. Thanks :)
Still not working on the laptop though. But I'll get it to work eventually.
Thank you for the patience.

---

### Post by narcisgarcia on 2011-07-10
I've tried to use the files and steps provided by cre8or in Ubuntu 11.04, and with lsusb the device is detected as:
> 12d1:14d1 Huawei Technologies Co., Ltd.

...but Network Manager doesn't notice any change nor shows any "mobile broadband" option in the nets list. The "ifconfig" command doesn't list any additional device too. I've also tried to unplug and plug again the usb modem.

---

### Post by DesireeMeerkatMaverick on 2011-07-22
> **cre8or said:**
> I got it working after days of painful research
So the solution.
You have to trick linux into thinking it is a different modem, this involves installing usb_modeswitch and editing 3 files
The first file 
**sudo gedit /etc/usb_modeswitch.conf**
add the following lines
DefaultVendor= 0x12d1
DefaultProduct=0x14d1
TargetVendor= 0x12d1
TargetProduct= 0x1c05
CheckSuccess=20
MessageContent="55534243123456780000000000000011060000000000000000000000000000"


The second file you will need to create
**sudo gedit /etc/usb_modeswitch.d/12d1:14d1**

Then add the following lines - yes almost the same as above
################################################## ######
# Huawei K3770

DefaultVendor= 0x12d1
DefaultProduct=0x14d1

TargetVendor= 0x12d1
TargetProduct= 0x1c05
CheckSuccess=20
MessageContent="55534243123456780000000000000011060000000000000000000000000000"

And finally the last file
**sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules**
Add the line


# Huawei Ek3770
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14d1", RUN+="usb_modeswitch '%b/%k'"

I rebooted after this and it works.
I did notice that if you startup with the modem it sometimes does not find it, just pull it out and put it back in.
It works with network manager
Hi there Cre8tor

I went through the steps as you indicated. There is no change. My computer still doesn't recognize the device. I've been reading Keir's 'Guide to Ubuntu" but haven't found anything yet.

Just wanted to make sure the files I downloaded from Beta  Vine Data Cards are correct; they are as follows:

python-messaging_0.5.9-1_all.deb
bcm_2.99.12-1.all.deb
usb-modeswitch-data_20100826-1betavine1_all.deb
wader-core_0.5.5-1_all.deb 

Thanks
DesireeMeerkatMaverick

---

### Post by DesireeMeerkatMaverick on 2011-07-22
> **DesireeMeerkatMaverick said:**
> Hi there Cre8tor

I went through the steps as you indicated. There is no change. My computer still doesn't recognize the device. I've been reading Keir's 'Guide to Ubuntu" but haven't found anything yet.

Just wanted to make sure the files I downloaded from Beta  Vine Data Cards are correct; they are as follows:

python-messaging_0.5.9-1_all.deb
bcm_2.99.12-1.all.deb
usb-modeswitch-data_20100826-1betavine1_all.deb
wader-core_0.5.5-1_all.deb 

Thanks
DesireeMeerkatMaverick
PS    I'm going through all the documents in this thread. There's a lot of  information and a lot to digest. Pretty sure the solution you posted for Narcisgarcia will do the trick.

DesireeMeerkatMaverick

---

### Post by narcisgarcia on 2011-07-23
What are the Beta Vine packages?
Where is the repository or project's web?

---

### Post by DesireeMeerkatMaverick on 2011-07-23
> **narcisgarcia said:**
> What are the Beta Vine packages?
Where is the repository or project's web?
_[COLOR=Black]**RE: Vodafone Mobile Broadband USB Stick K3770**[/COLOR]_


Here you go, 

[http://www.betavine.net/datacards/index.php/Main_Page](http://www.betavine.net/datacards/index.php/Main_Page). 
Did you  not have these packages?

regards
DesireeMeerkatMaverick

---

### Post by narcisgarcia on 2011-07-24
Ok, then which is the complete steps to make work a K3770?
Does Ubuntu's NetworkManager must be removed before installing Vodafone's Connection Manager 2.99 ?

---

### Post by DesireeMeerkatMaverick on 2011-07-24
> **narcisgarcia said:**
> Ok, then which is the complete steps to make work a K3770?
Does Ubuntu's NetworkManager must be removed before installing Vodafone's Connection Manager 2.99 ?
_**Re: **_

---

### Post by DesireeMeerkatMaverick on 2011-07-24
> **DesireeMeerkatMaverick said:**
> _**Re: **_
[U][B]Re: Betavine is  not a driver ...

[/B][/U] Right now I'm just totally confused. I've got the Sakis 3g, python messaging, wader-core, usb_modeswitch-data, as well as the bcm_2.99.12-1, as well as usb_modeswitch conf. and some other usb_modeswitch-data. I assumed the drivers I  was looking for initially were in these files. So let me start from the top. I have no  access to the internet via my PC which is where my Ubuntu 10.10 Maverick Meerkat is.  My internet access is via my laptop and Windows XP. This is my first exposure to Ubuntu and I'm having a lot of difficulty trying to figure out what exactly the issue is and why I haven't been able to connect via my USB stick.  My  USB stick is Huawei K3770. The provider is Vodacom South Africa. I've had a Linux IT specialist try to set it up but he said the issue was that the drivers and in order for  me to get the drivers I'd have to take my  PC to Vodacom Head Offices in Midrand to  have them installed. Vodacom has told me they don't support Ubuntu so I'm unable to get the drivers from them.  I downloaded the Sakis  3G file as well as the  Betavine cards but have had no luck because I'm very confused about the use of the terminal and  commands. I've been reading up on the documentation as well as trying to follow the thread in this discussion. However tonight I am more confused than ever and don 't have a clue as to the next steps or how to  get my PC to have internet connectivity. If it is the drivers that are  missing, what are the names of the drivers and will I be able to download  them onto a flash stick and then plug this into my PC, if this is possible how do I go about getting my PC to install the drivers from the stick or home  directory via the terminal. I'm just totally confused right now. Hope somebody  can give me some information that helps untangle and untie  my current state of confusion. 


hoping for clarity and thanking in advance
DesireeMeerkatMaverick

---

### Post by roberthanekom on 2011-07-25
Hi Desiree,
This is probably not going to help you. Though mine is working, I could honestly not tell you exactly how.

Initially I accessed the internet using the sim card in my nokia; set on OVI Suite mode, Ubuntu picks it up in seconds.

I am hoping that me explaining my process would give someone that has more knowledge of these things a clue of what needs to be done in order to get yours (and mine on my laptop) going.

I also started google'n around for a fix. Found the reference to Sakis3G and Betavine, tried it with no luck. Then I got the bright idea to consult Ubuntu Forums (should have done it from the start) and things started to look promising after doing the edits suggested by cre8tor [post #19, this thread], but still not working. I then queried his post and he gave the files [post #26 and #27, this thread].

Now this where it got fuzzy. I copied the files; still not working. Tried adding connections, deleting connections, rebooting ever so often.

Then suddenly, with another reboot, it started to work! (Even though I was relieved, I got that all to familiar "Windows: what-the...?" feeling).

I've been trying to get it working on my wife's laptop for the past two weeks with no luck. I even Installe Mint 11, then Ubuntu 10 and then Ubuntu 11 again with no luck

So I guess I am where narcisgarcia were in post #29.[URL="http://ubuntuforums.org/member.php?u=396492"]
[/URL]

---

### Post by DesireeMeerkatMaverick on 2011-07-25
> **roberthanekom said:**
> Hi Desiree,
This is probably not going to help you. Though mine is working, I could honestly not tell you exactly how.

Initially I accessed the internet using the sim card in my nokia; set on OVI Suite mode, Ubuntu picks it up in seconds.

I am hoping that me explaining my process would give someone that has more knowledge of these things a clue of what needs to be done in order to get yours (and mine on my laptop) going.

I also started google'n around for a fix. Found the reference to Sakis3G and Betavine, tried it with no luck. Then I got the bright idea to consult Ubuntu Forums (should have done it from the start) and things started to look promising after doing the edits suggested by cre8tor [post #19, this thread], but still not working. I then queried his post and he gave the files [post #26 and #27, this thread].

Now this where it got fuzzy. I copied the files; still not working. Tried adding connections, deleting connections, rebooting ever so often.

Then suddenly, with another reboot, it started to work! (Even though I was relieved, I got that all to familiar "Windows: what-the...?" feeling).

I've been trying to get it working on my wife's laptop for the past two weeks with no luck. I even Installe Mint 11, then Ubuntu 10 and then Ubuntu 11 again with no luck

So I guess I am where narcisgarcia were in post #29.[URL="http://ubuntuforums.org/member.php?u=396492"]
[/URL]
Hi Robert

I saw the files he'd posted for you and was sure that I could try them also, so could you tell me exactly what you did please? I will transfer the files onto my memory stick which I  will then plug into my PC and place in a directory. I guess my question relates pragmatically,  do I open the terminal and type in the  commands to  fetch the newly placed files? Having fetched them what do I do with the files  next? I guess my question is what is the exact process, do I keep the terminal open, how do I save the commands in the  terminal, do I close out of the terminal and then reboot? 
Apart from a basic HTML programming course I did more than a decade ago I have very little programming knowledge and so it's the process and the precise steps that totally flummox me. I got totally lost in the  commands and the guide book to Ubuntu.  I'm pretty sure there will be more replies and I'm just as sure that before too long we will have the problem totally sorted and solved!

regards
DesireeMeerkatMaverick

---

### Post by roberthanekom on 2011-07-25
I'll give it a go. I'm no expert so if there is an easier way, anybody, please do tell.

First you need to understand that you are faced with a lack of permissions, so you cannot just drag-and-drop them like in windows. That is why you will need to use the command line in Terminal. Each command you will start with *"sudo "*. This tells the OS that you want to execute the command as the administrator. Also bear in mind that Linux is 'case sensitive'. I.e., "sudo" and "Sudo" and "sUdo" for instance are three different things to the OS.

Ok, first, working not in the terminal, make a folder with the name "files" on your desktop and and copy the files "12d1_14d1", "40-usb_modeswitch.rules" and "usb_modeswitch.conf" into this folder. Use drag-and-drop.

Now rename the file "12d1_14d1" to "12d1:14d1" (<right-click>, <Rename> or highlight and press <f2>).

Start Terminal. Enter the following, one line at a time, on the command line (you can copy and paste. Hint: in Terminal <Ctrl,V> don't work; use <right-click>,<paste>).

[COLOR=Sienna][I]sudo cp ~/Desktop/files/usb_modeswitch.conf /etc
sudo cp ~/Desktop/files/12d1:14d1 /etc/usb_modeswitch.d
sudo cp ~/Desktop/files/40-usb_modeswitch.rules /lib/udev/rules.d[/I][/COLOR]
[COLOR=Black]
You'll be prompted for your password after the first line.

Now re-boot, plug in the K3770 and wait for the magic...
[/COLOR]

---

### Post by DesireeMeerkatMaverick on 2011-07-26
> **roberthanekom said:**
> I'll give it a go. I'm no expert so if there is an easier way, anybody, please do tell.

First you need to understand that you are faced with a lack of permissions, so you cannot just drag-and-drop them like in windows. That is why you will need to use the command line in Terminal. Each command you will start with *"sudo "*. This tells the OS that you want to execute the command as the administrator. Also bear in mind that Linux is 'case sensitive'. I.e., "sudo" and "Sudo" and "sUdo" for instance are three different things to the OS.

Ok, first, working not in the terminal, make a folder with the name "files" on your desktop and and copy the files "12d1_14d1", "40-usb_modeswitch.rules" and "usb_modeswitch.conf" into this folder. Use drag-and-drop.

Now rename the file "12d1_14d1" to "12d1:14d1" (<right-click>, <Rename> or highlight and press <f2>).

Start Terminal. Enter the following, one line at a time, on the command line (you can copy and paste. Hint: in Terminal <Ctrl,V> don't work; use <right-click>,<paste>).

[COLOR=Sienna][I]sudo cp ~/Desktop/files/usb_modeswitch.conf /etc
sudo cp ~/Desktop/files/12d1:14d1 /etc/usb_modeswitch.d
sudo cp ~/Desktop/files/40-usb_modeswitch.rules /lib/udev/rules.d[/I][/COLOR]
[COLOR=Black]
You'll be prompted for your password after the first line.

Now re-boot, plug in the K3770 and wait for the magic...
[/COLOR]
Hi Robert

There appears to be something else up with  either my terminal or the system. I did as you  suggested. The files folder is on my desktop and when I open it I see the files as I copied and pasted them, also renamed the "12d114d1" to "12d1:14d1".  I noticed that in your documentation  there was an underscore between the 12d1 and the 14d1, on my stick the underscore was absent. Not sure whether this is an issue but nonetheless renamed. So the 'files' folder is on my desktop with the required files. After typing in the  first line I do get prompted for my password, after typing in the 2nd line (12d1:14d1) the following is rendered 'cp: cannot stat '/home/desiree/Desktop/files/12d1:14d1':no such file or directory.  Any suggestions?

---

### Post by DesireeMeerkatMaverick on 2011-07-26
> **DesireeMeerkatMaverick said:**
> Hi Robert

There appears to be something else up with  either my terminal or the system. I did as you  suggested. The files folder is on my desktop and when I open it I see the files as I copied and pasted them, also renamed the "12d114d1" to "12d1:14d1".  I noticed that in your documentation  there was an underscore between the 12d1 and the 14d1, on my stick the underscore was absent. Not sure whether this is an issue but nonetheless renamed. So the 'files' folder is on my desktop with the required files. After typing in the  first line I do get prompted for my password, after typing in the 2nd line (12d1:14d1) the following is rendered 'cp: cannot stat '/home/desiree/Desktop/files/12d1:14d1':no such file or directory.  Any suggestions?
Hi  Robert

I went through  the  steps a second time and this time there was no message regarding the absence of  the 12d1:14d1 files. I completed the entire process without interruption rebooted but no magic. I  will give it another go and keep rebooting for awhile see if  anything 'comes together'. 

thanks
Desiree

---

### Post by afrodeity on 2011-07-27
Hi Desiree,

There really should be a better way to get this going. You can also try subscribing to the ubuntu-za mailing list. Some of the people there may be more familiar with Vodacom issues. [https://lists.ubuntu.com/mailman/listinfo/ubuntu-za](https://lists.ubuntu.com/mailman/listinfo/ubuntu-za)

Otherwise check [this]("http://developer.vodafone.com/discuss/question/188/installing-vodafone-mobile-connect-usb-modem-huawei-e272-on-ubuntu-804/") out

---

### Post by karla0nlinux on 2011-08-11
I have followed this thread in some desperation, trying to get myself connected with my new K3770. My HP mini runs on Ubuntu 10.04.  I followed Cre8tor's advice, checked myself using alexfish's post #30 on [http://ubuntuforums.org/showthread.php?p=10793568#post10793568](http://ubuntuforums.org/showthread.php?p=10793568#post10793568).  As far as I could tell, my modem did not switch, despite having all the instructions to do so.  Tonight I finally installed Sakis3G:

In Terminal, I entered the following lines successively:
wget "[http://www.sakis3g.org/versions/latest/i386/sakis3g.gz](http://www.sakis3g.org/versions/latest/i386/sakis3g.gz)"
echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c
gunzip sakis3g.gz
chmod +x sakis3g
./sakis3g --interactive

The last command opens up a window with several options.  I created a shortcut to my desktop, then disconnected my working modem, connected the K3770, and waited for those double flashes of green to show that it was picked up.  Then I followed the prompts to create a new connection.  After it had all my information, it tried to connect and failed (can't guarantee that I gave it all the correct instructions - some questions I guessed), but I noticed that my modem finally showed an intermittent flash of blue.  That inspired me to try the connection that I had previously set up on Network Manager and finally, it showed the Mobile Broadband connections as available.  And connected successfully.

An interesting observation: up to this point, if I typed lsusb into the Terminal, the K3770's target lines came up as 12d1:14d1.  I checked it after I had installed Sakis, and it came up as 12d1:14c9 - so it had finally switched!

I'm in South Africa and on Vodacom.  The Sakis3G website lists all the countries and providers they're set up for: [http://www.sakis3g.org/](http://www.sakis3g.org/) 

Good luck!

---

### Post by pdc on 2011-08-11
Well done to karlaonlinux for getting sakis 3g running so smoothly and well; I have used it and found it excellent;

all these usb broadband dongles are first seen as virtual CD-ROM devices; as they contain windows (and mac?) software;

their ID needs to be "flipped" to be seen;

increasingly the ID of many devices is built-in to distros; so the distro will auto-flip as a background function;

before that; the means to flip was:

**usb_modeswitch** it is the means *par excellence* to do this (run from S Africa I think?)

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

so: 

1) some usb dongles are auto-recognised when you plug them in
2) if not, download and install usb_modeswitch (details on the above)

or 
3) sakis 3g contains usb_modeswitch and other magic as a dialler
4) betavine; for vodafone only; contains usb_modeswitch and is yet another alternative dialler to NetworkManager 

the device that started this thread **IS LISTED** in usb_modeswitch; it is there;it is recognised; it exists;

> # Vodafone/Huawei K3770
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14d1", RUN+="usb_modeswitch '%b/%k'"


here is its entry in the usb_modeswitch data package

nobody should need to edit anything ................

---

### Post by SA_LinuxNewb on 2011-08-27
Hi.

I'm new here and I also purchased the Vodacom K3770 in SA.
On Windows XP it works fine, but i want to use it on Ubuntu (11.04) because I got a really old Laptop (MAXDATA 9100) and Ubuntu works way faster than XP.

I think i read all the Threads about K3770 but I'm getting nowhere. Sometimes its to complicated and I dont know how to try the solutions (and I dont want to screw up my linux).

My Situation is like that:
I have XP and Ubuntu installed on my Laptop and I'm currently online on XP. My only connection is with this Stick because we haven't got any Internet here.

When I plug in the Modem on Ubuntu, then the green Light flashes so it finds a connection. But Ubuntu only shows a "CD" with Windows and Mac Drivers on it.

I installed Sakis3g and tried everything there. Switching Modem (which works without Error, but doenst help) and setting up 3g Connctions. 
When I set up a 3g Connection it shows The Huawai Vodacom stick but then it writes "Error: Couldnt find Device" (or something like that, I dont remember exactly). So it doesnt work at all.

In the Network Manager (I hope thats the correct name, I got a German Ubuntu) it doesnt find a Modem Device at all.

What should I do? (Plz step by step help, because I'm new to Ubuntu, I only now the basics.. root, sudo, ls, cd, ...)

PLEASE help me, because I tried Ubuntu and i really like it and I dont wanna switch back to Windows, but if that doesn't work i have to. Ubuntu does everything so easy and it's working so nice, but in that case I can't go without Windows. :(

[SIZE=1]Sry for my English, I'm from Austria and a Voluntary in SA, so my English isn't that good. :)[/SIZE]

---

### Post by pdc on 2011-08-27
with the modem plugged in, can you open a terminal:

go to the Accessories section of the menu, and find Terminal;

if you get it opened, type

> lsusb and hit the ENTER key

tell us if the modem shows as 

> 12d1:14d1

or 

> 12d1:14c9

.........if you have sakis3g installed, it *should* flip the K3770 so it is seen as a modem ..............

---

### Post by sherif.louis on 2011-08-27
Hello everyone, 

I have been reading into the usb_modeswitch documentation here:
[http://www.draisberghof.de/usb_modeswitch/#usage](http://www.draisberghof.de/usb_modeswitch/#usage)

i'm using ubuntu 11.04

i followed cre8or's procedure to add the K3770 to udev rules file
and creating the configuration files and nothing happens automatically

i realized that the usb id only changes when i explicitly run usb_modeswitch -c /etc/usb_modeswitch.conf

the documentation says that the usb_modeswitch.conf file is a global configuration file which is used for logging or enable/disabling switching all together
"a global config file to enable extensive logging when troubleshooting, or to disable switching alltogether (mostly to access the install part of devices)"

the interesting part is here:

this is where it all happens:
/usr/share/usb_modeswitch - a folder containing the individual setup information files per device, named according to the IDs and possibly further identity tokens (to resolve known ambiguities). If your device ID shows up in one of the file names, chances are your device is supported even if the model or brand does not match. 

i added the 12d1:14d1 file created earlier to the config.tar.gz residing under /usr/share/usb_modeswitch and now it switches automatically when i insert the usb stick...

thanks Cre8or for the enormous effort :-)

---

### Post by SA_LinuxNewb on 2011-08-27
@pdc

I tried it but it wouldnt switch.. it says "Modem switched" but it didnt switch. :/

I copied it on a USB Stick so you can see it yourself.
[SIZE=1][SIZE=2][PHP]//before
dominik@dom:~$ lsusb
Bus 004 Device 002: ID 0483:0321 SGS Thomson Microelectronics 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 12d1:14d1 Huawei Technologies Co., Ltd. 
Bus 001 Device 002: ID 1e3d:2092  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

//"Modem switched" 
dominik@dom:~$ lsusb
Bus 004 Device 002: ID 0483:0321 SGS Thomson Microelectronics 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 12d1:14d1 Huawei Technologies Co., Ltd. 
Bus 001 Device 002: ID 1e3d:2092  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/PHP][/SIZE][SIZE=2]So it didnt switched..
what can i do do make it switch?

edit: I used the GUI for Sakis3g.. if that matters..
[/SIZE][/SIZE]

---

### Post by sherif.louis on 2011-08-27
you should try to add the configuration file 12d1:14d1 to the configPack.tgz file.

did Sakis work straight away without the switching?

---

### Post by SA_LinuxNewb on 2011-08-27
@sherif.louis:
did u mean me?

where can i find the how-to for adding the configuration file?

---

### Post by alexfish on 2011-08-27
Hi all 

Natty user please follow this 
**Re: Natty, known bugs, fixes and work arounds**
[http://ubuntuforums.org/showpost.php?p=10793568&postcount=30](http://ubuntuforums.org/showpost.php?p=10793568&postcount=30)

then follow the instructions for the usb_modeswitch.d files and how to add the rule
using the files supplied by cre8tor  post #[**30**]("http://ubuntuforums.org/showpost.php?p=11075516&postcount=30") . can possible ignore the .conf file
This will also may apply if users have downloaded the latest data pack from the debian repos
please note the files listed at the site (
> /lib/udev/rules.d/40-usb_modeswitch.rules
 /usr/share/bug/usb-modeswitch-data/presubj 
/usr/share/doc/usb-modeswitch-data/NEWS.Debian.gz
 /usr/share/doc/usb-modeswitch-data/README.Debian
 /usr/share/doc/usb-modeswitch-data/README.gz
 /usr/share/doc/usb-modeswitch-data/changelog.Debian.gz
 /usr/share/doc/usb-modeswitch-data/changelog.gz
 /usr/share/doc/usb-modeswitch-data/copyright
 [COLOR=Blue]/usr/share/usb_modeswitch/configPack.tar.gz[/COLOR]I  still recommend installing sakis3g, probably still one of the best  scripts for detecting and switching the modem ,and often connects when  Network Manager can't 

regards

alexfish

---

### Post by pdc on 2011-08-27
Hi SA_LinuxNewb;

we would all wish linux things worked easily and well;

particularly for those who have recently joined linux!

seems like we are tying ourselves in knots here;

I recommend you join the usb_modeswitch forum;

go here;

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

join up;

I get the sense that Josh is based in SA: Josh oversees the programme and the forum;

give him reference to this forum;

tell him your issues;

he can help you sort this;

when you get it sorted, come back here and tell us

best wishes

**PS** one final request:

open a terminal

copy and paste this command

> sudo usb_modeswitch -h

into the terminal; (you will be asked for your sudo password)

copy and paste back here what you get .........I am hoping you should see version 1.1.9 or something similar .............

---

### Post by SA_LinuxNewb on 2011-08-28
Ok. i ll register there and ask for help.

here the thing you requested:

```
dominik@dom:~$ sudo usb_modeswitch -h
[sudo] password for dominik: 

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.6 (C) Josua Dietze 2010
 * Based on libusb0 (0.1.12 and above)
```so its an older version. maybe thats the problem..
maybe i just have to install a new one, but i dont know how :)
because i read [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=679&postdays=0&postorder=asc&highlight=k3770&start=15](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=679&postdays=0&postorder=asc&highlight=k3770&start=15) here that there was a mistake with the k3770, so mabye a newer version works.

i also tried some thing from alexfish's first link. i dont know, but i dont think it went well :D

here is the copy from the terminal. i dont think someone will read it, but i have saved it.
thx 4 ur help

edit:
ok. maybe it really just the version and i should update. can u give me step to step instructions so i dont mess the installation up?

---

### Post by alexfish on 2011-08-28
> **SA_LinuxNewb said:**
> Ok. i ll register there and ask for help.

here the thing you requested:

```
dominik@dom:~$ sudo usb_modeswitch -h
[sudo] password for dominik: 

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.6 (C) Josua Dietze 2010
 * Based on libusb0 (0.1.12 and above)
```so its an older version. maybe thats the problem..
maybe i just have to install a new one, but i dont know how :)
because i read [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=679&postdays=0&postorder=asc&highlight=k3770&start=15](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=679&postdays=0&postorder=asc&highlight=k3770&start=15) here that there was a mistake with the k3770, so mabye a newer version works.

i also tried some thing from alexfish's first link. i dont know, but i dont think it went well :D

here is the copy from the terminal. i dont think someone will read it, but i have saved it.
thx 4 ur help

edit:
ok. maybe it really just the version and i should update. can u give me step to step instructions so i dont mess the installation up?
Hi

lets take a fresh look

since usb_modeswitch is on the system can try direct from the terminal

list the device with the lsusb command
```
lsusb
``` if it shows 12d1:14d1 execute the usb_modeswitch
```
usb_modeswitch -v 0x12d1 -p 0x14d1 -M 55534243123456780000000000000011060000000000000000000000000000
```
see if the id's have changed with the lsusb command

also list the device with this command
```
usb_devices
```locate the device from the listing and post only those lines

will then look at the configuration files

regards

alexfish

---

### Post by SA_LinuxNewb on 2011-08-28
IT WORKED!!

i switched it with the command u posted:

> //after the command: 
Bus 001 Device 004: ID 12d1:1c05 Huawei Technologies Co., Ltd. so it switched.. great.. 
it tried to set it up via network manager (i hope thats the correct name for the GUI network tool) but it didnt find the modem

so i tried sakis3g..

and because it was switched properly i could establish a connection and making my first post with ubuntu..
so THANKS!!

and now the gui network tool find the modem too...

but i got some questions..
could the update from modeswitch work too? (so it already knows my device, because its a newer version)

or will i have to do the "terminal modeswitch" after every reboot?

here the usb-devices u asked for:
```

//usb-devices: 
dominik@dom:~$ usb-devices 
 
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6 
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0002 Rev=02.06 
S:  Manufacturer=Linux 2.6.38-10-generic ehci_hcd 
S:  Product=EHCI Host Controller 
S:  SerialNumber=0000:00:1d.7 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
 
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0 
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=12d1 ProdID=1c05 Rev=01.02 
S:  Manufacturer=HUAWEI 
S:  Product=Vodafone Mobile Broadband (Huawei) 
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA 
I:  If#= 0 Alt= 0 #EPs= 3 Cls=02(commc) Sub=02 Prot=ff Driver=(none) 
I:  If#= 1 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=(none) 
I:  If#= 2 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=(none) 
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage 
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage 
 
T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  3 Spd=480 MxCh= 0 
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1e3d ProdID=2092 Rev=01.00 
S:  Manufacturer=CBM      
S:  Product=Flash Disk       
S:  SerialNumber=2216100094CAD203 
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA 
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage 
 
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2 
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0001 Rev=02.06 
S:  Manufacturer=Linux 2.6.38-10-generic uhci_hcd 
S:  Product=UHCI Host Controller 
S:  SerialNumber=0000:00:1d.0 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
 
T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2 
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0001 Rev=02.06 
S:  Manufacturer=Linux 2.6.38-10-generic uhci_hcd 
S:  Product=UHCI Host Controller 
S:  SerialNumber=0000:00:1d.1 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
 
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2 
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0001 Rev=02.06 
S:  Manufacturer=Linux 2.6.38-10-generic uhci_hcd 
S:  Product=UHCI Host Controller 
S:  SerialNumber=0000:00:1d.2 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 
 
T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0 
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1 
P:  Vendor=0483 ProdID=0321 Rev=01.92 
S:  Manufacturer=Generic 
S:  Product=USB Mass Storage Device 
S:  SerialNumber=7777777777777777 
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA 
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage 
 

```again THANKS!

is there a way to log how much traffic i used? because i have only 2gig per month and i dont want to pay more than necessary..
is there a way to "share" the connection like on xp? (at first i shared it with xp to a wlan router, so my friend can be online with the ipad too)
(i know the last 2 are little bit off topic, but i have to ask :D)

edit:
ok. if I reboot everything is back to "not working"
when i connect with sakis3g and then disconnect i can establish a conncection with the network manager..
its nice, because i see the connectivity and stuff.. :)
ill try to reboot, maybe it will work again without a manual modem switch..

edit2:
doesnt work :D
so if i reboot i have to do everthing again..

---

### Post by alexfish on 2011-08-28
Hi SA_LinuxNewb

> from the usb_device note the
I:  If#= 0 Alt= 0 #EPs= 3 Cls=02(commc) Sub=02 Prot=ff Driver=(none) 
I:  If#= 1 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=(none) 
I:  If#= 2 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=(none) 
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage 
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage indicators are :suitable drivers do not have device (by ids), notice it works with sakis3g (looks like sakis3g is loading a suitable driver or using the default serial driver

use the commands to switch the device , then use sakis3g

can post the details of the usb_devices command after connecting or configuring the device with sakis3g

will then look at all the info in detail

regards

alexfish

---

### Post by SA_LinuxNewb on 2011-08-29
alright, i used the manual modeswitch and then used sakis3g to set up the modem. then i connected with the network manager..

here is the code:

```
dominik@dom:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-10-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c05 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=Vodafone Mobile Broadband (Huawei)
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=02(commc) Sub=02 Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1e3d ProdID=2092 Rev=01.00
S:  Manufacturer=CBM     
S:  Product=Flash Disk      
S:  SerialNumber=2216100094CAD203
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-10-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-10-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-10-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=0483 ProdID=0321 Rev=01.92
S:  Manufacturer=Generic
S:  Product=USB Mass Storage Device
S:  SerialNumber=7777777777777777
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```

thx 4 ur help

greetings dominik

---

### Post by alexfish on 2011-08-29
hi SA_LinuxNewb

can try the following
```
sudo gedit /etc/usb_modeswitch.d/12d1:14d1
```if file contains data delete existing code,

copy and paste this code

```
########################################################
#  Vodafone Mobile Broadband USB stick K3770 (Huawei)

DefaultVendor= 0x12d1
DefaultProduct=0x14d1

TargetVendor=  0x12d1
TargetProduct= 0x1c05

CheckSuccess=20

MessageContent="55534243123456780000000000000011060000000000000000000000000000"
```
save and exit
check the rules
```
sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules
```
look through the listing for line same as
> ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14d1", RUN+="usb_modeswitch '%b/%k'"
if the line does not exist add the following code within the main rules below the > (LABEL="modeswitch_rules_begin")
```
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14d1", RUN+="usb_modeswitch '%b/%k'"
```
save and exit reboot with the device connected

check to see if the device ids have changed to 12d1:1c05
```
lsusb
```if the device has not switched run sakis3g 

if sakis3g fails then will have to run usb_modeswitch manually then use sakis3g as before

**if the device has switched after boot**

open up a terminal and find out the device status with the usb-devices command
```
usb-devices
```need to see if there are lines similar to
> T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c05 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=Vodafone Mobile Broadband (Huawei)
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=02(commc) Sub=02 Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

if part of the listing shows " Driver=(none) "

try this code

```
sudo su
modprobe option
echo "12d1 1c05" > /sys/bus/usb-serial/drivers/option1/new_id
```

if successful then should be able to connect with Network Manager

post all info

regards

---

### Post by SA_LinuxNewb on 2011-08-29
alright. i changed the rules and im gonna reboot now (just writing now in case the thing doesnt work :)

when i did the 2 commands i got warnings:
(i dont know if thats important, so im gonna show u)

> dominik@dom:~$ sudo gedit /etc/usb_modeswitch.d/12d1:14d1

(gedit:7307): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Datei »/root/.local/share/recently-used.xbel.Q9JJ0V« konnte nicht angelegt werden: Datei oder Verzeichnis nicht gefunden

(gedit:7307): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Datei oder Verzeichnis nicht gefunden

(gedit:7307): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Datei »/root/.local/share/recently-used.xbel.54H20V« konnte nicht angelegt werden: Datei oder Verzeichnis nicht gefunden

(gedit:7307): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Datei oder Verzeichnis nicht gefunden
> dominik@dom:~$ sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules 

(gedit:7416): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Datei »/root/.local/share/recently-used.xbel.DAY40V« konnte nicht angelegt werden: Datei oder Verzeichnis nicht gefunden

(gedit:7416): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Datei oder Verzeichnis nicht gefunden

(gedit:7416): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Datei »/root/.local/share/recently-used.xbel.04TR0V« konnte nicht angelegt werden: Datei oder Verzeichnis nicht gefunden

(gedit:7416): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Datei oder Verzeichnis nicht gefundeni'll edit after the reboot..

ok, first edit: the warning (in german) means: "file or directory wasn't found"

edit2:
damnit, now im online with xp.. :/
it didnt switched after boot
then i tried to switch it with sakis.. didnt switch again
then i tried it to switch in terminal with modeswitch..
i got this:
> dominik@dom:~$ sudo usb_modeswitch -v 0x12d1 -p 0x14d1 -M 55534243123456780000000000000011060000000000000000000000000000

Looking for default devices ...
 Found devices in default mode, class or configuration (1)
Accessing device 002 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using endpoints 0x0f (out) and 0x8f (in)
Using endpoints 0x0f (out) and 0x8f (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

^Cdominik@dom:~$
i "stopped" it with control+c

so it didnt switch again and i cant use sakis either... :(

here the part of the usb-devices:
> T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14d1 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=Vodafone Mobile Broadband (Huawei)
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)
maybe it helps..

alright, thanks again 4 help.. :)

---

### Post by alexfish on 2011-08-29
hi

did you check the device ids before trying the usb_modeswitch

can try plugging the device in after boot

the try the procedures again

regards

alexfish

---

### Post by SA_LinuxNewb on 2011-08-29
what did you mean by id?
the lsusb? yeah i checked that.. wasnt switched all the time.. (always 12d1:14d1)

ok. ill try plugging it in after booting

edit:
back on with ubuntu =D

so if i plug it in it doesnt switch, but i can set up a connection with sakis3g (which i couldnt before, because i had to manually switch it and now sakis3g can do it on his own  :)

here is copy of the usb-devices:
(after sakis)
> T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c05 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=Vodafone Mobile Broadband (Huawei)
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=02(commc) Sub=02 Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


edit2:
ok thats strange. i replugged it. and it shows 12d1:14d1 (as always). when i try to switch it with sakis ("Switch Modem") it says switched to 12d1:14d1.. good job. :/
but when press "set up modem" or "connect 3g" it swtiches properly and works..

---

### Post by alexfish on 2011-08-29
ok looks as if the etc/usb_modeswitch file is working with sakis3g

not sure why there is a problem with plugging the device before boot

keep using sakis3g for now , and I need to look further into the installed usb_modeswitch

but also try updating the system when you got a connection , then reinstall usb_modeswitch from synaptic package manager , do not upgrade the usb_modeswitch at present, the device id's are not in the data base (I think says he ,?)

after updating check that the [FONT=monospace]"[/FONT]/etc/usb_modeswitch.d/12d1:14d1" files still exists if the device fails to switch

see what happens

also need look further as to what is happening at the Ubuntu end , also suggest contacting the usb_modeswitch forum , josh may be able to debug the problem when the device is plugged in at boot ( may  be a storage delay problem IE: the device needs time to settle before the switching starts)

regards

alexfish

---

### Post by SA_LinuxNewb on 2011-08-30
alright then.. :D

i dont mind replugging it after boot and sakis3g works fine for me. so rly thank u for helping me.

i can't update right now, because im really low on traffic. :/

thx again

dominik

---

### Post by alexfish on 2011-09-02
hi again Dominic

have done some reading at the usb_modeswitch forum

had noticed this post , of interest : [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=729](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=729)

although a defferent device it may be worth trying to delay the switching of the modem
(although not sure what the outcome will be)

can try editing the usb_modeswitch.d file to include a delay
```
sudo gedit /etc/usb_modeswitch.d/12d1:14d1
```
add the following code to the file
```
WaitBefore=3
```save and exit.Then reboot with the device connected , and also connected after boot.

as said, not sure what the outcome will be, but can post any results

also can say if your system is a Lap Top (if so which make and model). or a desk top

regards

alexfish

---

### Post by SA_LinuxNewb on 2011-09-04
that doesnt change anything:

modem doesnt switch after boot and doesnt switch after plugging it in. but it still works with sakis3g..

i've got a laptop: MAXDATA 8100X and its really old

---

### Post by amiridina on 2011-09-29
hello I followed your instruction and it worked as it s said till message #52 Instead of it working I received the following 
Looking for default devices ...

 Found devices in default mode, class or configuration (1)
Accessing device 000 on bus 001 ...
Getting the current device configuration ...
Error: getting the current configuration failed (error -1). Aborting.

dina@dina-Compaq-Presario-C700-Notebook-PC:~$ usb_devices
No command 'usb_devices' found, did you mean:
 Command 'usb-devices' from package 'usbutils' (main)
usb_devices: command not found

Would you please help me.

Thank you.

---

### Post by kareempharmacist on 2011-10-14
It works perfectly and out-of-the-box on ubuntu 11.10 .....tried..all u have to do is to upgrade.
it works also on debian and any debian-based distribution.

---

### Post by foxy123 on 2011-11-25
> **kareempharmacist said:**
> It works perfectly and out-of-the-box on ubuntu 11.10 .....tried..all u have to do is to upgrade.
it works also on debian and any debian-based distribution.

I wonder what version of Ubuntu you've got (I mean 32 or 64)? Also what is you lsusb output for the modem? I cannot make this thing work. It seems to connect for a second and then nothing. I've got in the NetworkManager menu under geryed out Mobile Connections also greyed out Vodafone UK Edge or something like that (I'm away from my laptop).

---

### Post by foxy123 on 2011-11-28
I have managed to connect to teh Internet using Sakis3g. Do not really understand why it works with sakis but not with the NetworkManager. Anyway does anyone know how to automate the connection using sakis. I eman to do it with one click rather than to go through th eprocess of selecting things every time. I need to set it up for my wife and she's not the pc-savviest person :).

---

### Post by alexfish on 2011-11-28
> **foxy123 said:**
> I have managed to connect to teh Internet using Sakis3g. Do not really understand why it works with sakis but not with the NetworkManager. Anyway does anyone know how to automate the connection using sakis. I eman to do it with one click rather than to go through th eprocess of selecting things every time. I need to set it up for my wife and she's not the pc-savviest person :).
can use sakis3g with config file . have a look at the wiki pages

alexfish

---

### Post by foxy123 on 2011-11-29
> **alexfish said:**
> can use sakis3g with config file . have a look at the wiki pages

alexfish

Thanks a lot, it worked perfectly!

---

### Post by narcisgarcia on 2011-11-29
These are the simplest ways I found to use this device on Ubuntu Natty.

**Method 1:** Terminal commands with the device already plugged
(this must be done on every session)
```
sudo usb_modeswitch -v 0x12d1 -p 0x14d1 -V 0x12d1 -P 0x14c9 -M 55534243123456780000000000000011062000000100000000000000000000
sudo modprobe usbserial vendor=0x12d1 product=0x14c9

```

**Method 2:** Upgrading packages from 11.10 (Oneiric) to do it automatic
[LIST=1]
[*]Uninstall the package usb-modeswitch-data
[*]Install the next version package from [http://packages.ubuntu.com/oneiric/usb-modeswitch-data](http://packages.ubuntu.com/oneiric/usb-modeswitch-data)
[*]Install the next version package from [http://packages.ubuntu.com/oneiric/usb-modeswitch](http://packages.ubuntu.com/oneiric/usb-modeswitch)
[/LIST]

---

### Post by narcisgarcia on 2011-11-29
.

---

### Post by narcisgarcia on 2011-11-29
I've found in the ROM space of a K3770 this content in the file **version.ini**
```
[General]

info=30385

devices=60



[GE 0301]

vid=0AF0

pid=7011

vendor=O

name=GE 0301

version=9.3.0

copy=yes

convert=no



[GI 0301]

vid=0AF0

pid=7251

vendor=O

name=GI 0301

version=9.2.3

copy=yes

convert=no



[E3730 (GE 0421)]

vid=0AF0

pid=7301

vendor=O

name=E3730

version=9.3.3

copy=yes

convert=no



[K3760 (GI 0411)]

vid=0AF0

pid=7501

vendor=O

name=K3760

version=9.3.4

copy=yes

convert=no



[K3520 (E169) RAS]

vid=12D1

pid=1001

vendor=H

name=K3520 RAS

version=9.2.5

copy=no

convert=no



[E272]

vid=12D1

pid=1003

vendor=H

name=E272

version=9.2.3

copy=no

convert=no



[K3520 (E169) NDIS]

vid=12D1

pid=1401

vendor=H

name=K3520 NDIS

version=9.3.6

copy=no

convert=no



[E270+ with FW older than 11.806.06.00.00]

vid=12D1

pid=140C

vendor=H

name=E270+

version=9.3.7

copy=no

convert=no



[E510]

vid=12D1

pid=1411

vendor=H

name=E510

version=9.3.3

copy=no

convert=no



[M3710]

vid=12D1

pid=1418

vendor=H

name=M3710

version=9.3.6

copy=no

convert=no



[Non-converted E270+ or E182]

vid=12D1

pid=1446

vendor=H

name=E270+ or E182

version=9.4.2

copy=no

convert=no



[Converted K4505]

vid=12D1

pid=1464

vendor=H

name=K4505

version=9.4.4

copy=no

convert=no



[Converted K3765]

vid=12D1

pid=1465

vendor=H

name=K3765

version=9.4.3

copy=no

convert=no



[Converted R201]

vid=12D1

pid=1491

vendor=H

name=R201

version=10.0.300

copy=no

convert=no



[Converted E270+ or E182]

vid=12D1

pid=14AC

vendor=H

name=E270+ or E182

version=9.4.2

copy=no

convert=no



[Non-converted K3806]

vid=12D1

pid=14AD

vendor=H

name=K3806

version=10.1.104

copy=no

convert=no



[Converted K3806]

vid=12D1

pid=14AE

vendor=H

name=K3806

version=10.1.104

copy=no

convert=no



[Non-converted K4511]

vid=12D1

pid=14B7

vendor=H

name=K4511

version=10.2.100

copy=no

convert=no



[Non-converted K4605]

vid=12D1

pid=14C1

vendor=H

name=K4605

version=10.1.100

copy=no

convert=no



[Non-converted K5005]

vid=12D1

pid=14C3

vendor=H

name=K5005

version=10.3.0

copy=no

convert=no



[Non-converted K3771]

vid=12D1

pid=14C4

vendor=H

name=K3771

version=10.2.100

copy=no

convert=no



[Non-converted K4510]

vid=12D1

pid=14C5

vendor=H

name=K4510

version=10.2.100

copy=no

convert=no



[Converted K4605]

vid=12D1

pid=14C6

vendor=H

name=K4605

version=10.1.100

copy=no

convert=no



[Converted K5005]

vid=12D1

pid=14C8

vendor=H

name=K5005

version=10.3.0

copy=no

convert=no



[Converted K3770]

vid=12D1

pid=14C9

vendor=H

name=K3770

version=10.2.100

copy=no

convert=no



[Converted K3771]

vid=12D1

pid=14CA

vendor=H

name=K3771

version=10.2.100

copy=no

convert=no



[Converted K4510]

vid=12D1

pid=14CB

vendor=H

name=K4510

version=10.2.100

copy=no

convert=no



[Converted K4511]

vid=12D1

pid=14CC

vendor=H

name=K4511

version=10.2.100

copy=no

convert=no



[Non-converted K3770]

vid=12D1

pid=14D1

vendor=H

name=K3770

version=10.2.100

copy=no

convert=no



[Non-converted K3765]

vid=12D1

pid=1520

vendor=H

name=K3765

version=9.4.3

copy=no

convert=no



[Non-converted K4505]

vid=12D1

pid=1521

vendor=H

name=K4505

version=9.4.4

copy=no

convert=no



[Non-converted R201]

vid=12D1

pid=1523

vendor=H

name=R201

version=10.0.300

copy=no

convert=no



[Converted MC950D]

vid=1410

pid=4400

vendor=N

name=MC950D

version=9.2.3

copy=no

convert=no



[Non-converted MC950D]

vid=1410

pid=5010

vendor=N

name=MC950D

version=9.2.3

copy=no

convert=no



[Non-converted generic MiFi 2352]

vid=1410

pid=5041

vendor=N

name=MiFi 2352

version=9.4.3

copy=no

convert=yes



[Converted generic MiFi 2352]

vid=1410

pid=7001

vendor=N

name=MiFi 2352

version=9.4.3

copy=no

convert=no



[Converted Vodafone MiFi 2352]

vid=1410

pid=7003

vendor=N

name=MiFi 2352

version=9.4.4

copy=no

convert=no



[Converted K2525 (MZ10)]

vid=19D2

pid=0022

vendor=Z

name=K2525

version=9.3.3

copy=no

convert=no



[Converted K3520-Z (MF628) with maximal FW B07]

vid=19D2

pid=0025

vendor=Z

name=K3520-Z

version=9.3.3

copy=no

convert=no



[Non-converted K2525 (MZ10)]

vid=19D2

pid=0040

vendor=Z

name=K2525

version=9.3.3

copy=no

convert=no



[Converted K3565-Z (MF626) with maximal FW B07]

vid=19D2

pid=0052

vendor=Z

name=K3565-Z

version=9.3.4

copy=no

convert=no



[Converted K3520-Z (MF628) with minimal FW B08]

vid=19D2

pid=0055

vendor=Z

name=K3520-Z

version=9.3.4

copy=no

convert=no



[Converted K3565-Z (MF626) with minimal FW B08]

vid=19D2

pid=0063

vendor=Z

name=K3565-Z

version=9.3.7

copy=no

convert=no



[Non-converted K3520-Z with Win7 FW]

vid=19D2

pid=0098

vendor=Z

name=K3520-Z

version=9.4.4

copy=no

convert=no



[Non-converted K3565-Z with Win7 FW]

vid=19D2

pid=0099

vendor=Z

name=K3565-Z

version=9.4.4

copy=no

convert=no



[Non-converted K3765-Z with Win7 FW]

vid=19D2

pid=0100

vendor=Z

name=K3765-Z

version=9.4.4

copy=no

convert=no



[Non-converted K4505-Z]

vid=19D2

pid=0101

vendor=Z

name=K4505-Z

version=9.4.4

copy=no

convert=no



[Converted K4505-Z]

vid=19D2

pid=0104

vendor=Z

name=K4505-Z

version=9.4.4

copy=no

convert=no



[Non-converted K3805-Z]

vid=19D2

pid=1001

vendor=Z

name=K3805-Z

version=9.4.7

copy=no

convert=no



[Converted K3805-Z]

vid=19D2

pid=1002

vendor=Z

name=K3805-Z

version=9.4.7

copy=no

convert=no



[Non-converted K3570-Z]

vid=19D2

pid=1007

vendor=Z

name=K3570-Z

version=10.0.200

copy=no

convert=no



[Converted K3570-Z]

vid=19D2

pid=1008

vendor=Z

name=K3570-Z

version=10.0.200

copy=no

convert=no



[Non-converted K3571-Z]

vid=19D2

pid=1009

vendor=Z

name=K3571-Z

version=10.0.200

copy=no

convert=no



[Converted K3571-Z]

vid=19D2

pid=1010

vendor=Z

name=K3571-Z

version=10.0.200

copy=no

convert=no



[Non-converted K3806-Z]

vid=19D2

pid=1013

vendor=Z

name=K3806-Z

version=10.1.0

copy=no

convert=no



[Converted K3806-Z]

vid=19D2

pid=1014

vendor=Z

name=K3806-Z

version=10.1.0

copy=no

convert=no



[Non-converted K3565-Z (MF626) with minimal FW B08]

vid=19D2

pid=2000

iid=P673A2VDF_MS

vendor=Z

name=K3565-Z

version=9.3.7

copy=no

convert=no



[Non-converted K3765-Z]

vid=19D2

pid=2000

iid=P673A1VDF_MS

vendor=Z

name=K3765-Z

version=9.4.2

copy=no

convert=no



[Non-converted K3520-Z (MF628) with minimal FW B08]

vid=19D2

pid=2000

vendor=Z

name=K3520-Z

version=9.3.4

copy=no

convert=no



[Converted K3765-Z]

vid=19D2

pid=2002

vendor=Z

name=K3765-Z

version=9.4.2

copy=no

convert=no
```
The *Non-converted* sections correspond to the vendor (nc-vid) and product (nc-pid) found by **lsub** when modeswitch is not applied, and the *Converted* sections correspond to the vendor (c-vid) and product (c-pid) needed to use the modem.
For any Huawei modem it's possible to run:
```
sudo usb_modeswitch -v **<nc-vid>** -p **<nc-pid>** -V **<c-vid>** -P **<c-pid>** -M **<message-content>**
sudo modprobe usbserial vendor=0x**<c-vid>** product=0x**<c-pid>**
```
(I don't know what to apply for *message-content* on every different device)

---

### Post by matteosistisette on 2011-12-03
> **cre8or said:**
> I got it working after days of painful research
So the solution.
 
Hi,
 
I have the exactly same device and Ubuntu 10.10 but this solution didn't work for me.
 
I followed your solution step by step. All the mentioned files actually existed except for the one whose name is the device id, which is what I would expect.
 
I rebooted. I plug in the device and nothing happens. Network Manager doesn't show any option related to broadband mobile.
 
What may I be missing?
 
lususb shows this:
 
Bus 002 Device 006: ID 12d1:14d1 Huawei Technologies Co., Ltd.
 
which makes me think the usb_modeswitch thing is not working, otherwise it would show up as 12d1:14c9, right?
 
I copied and pasted your code into the files without understanding what it does, so is there any chance there is some typo in your code? Or what may I be missing? what could I check?
 
thanks
m.

---

### Post by matteosistisette on 2011-12-08
There are two errors in the procedure described by cre8or:

> **cre8or said:**
> 
The first file 
**sudo gedit /etc/usb_modeswitch.conf**
add the following lines
DefaultVendor= 0x12d1
DefaultProduct=0x14d1
TargetVendor= 0x12d1
**TargetProduct= 0x1c05**
CheckSuccess=20
MessageContent="**55534243123456780000000000000011060000000000000000000000000000**"



The target product is **14c9**, not 1c05, and the message was missing a "2" between the last 6 and the zeros, that is:

```
5553424312345678000000000000001106**2**000000100000000000000000000
```

Additionally, Mr Buggy VBullettin randomly adds extra spaces here and there, so there was also an extra space, (curiously exactly where the missing 2 was. Coincidence?) 

So the corrected version:


> 
**sudo gedit /etc/usb_modeswitch.conf**
add the following lines
```

DefaultVendor= 0x12d1
DefaultProduct=0x14d1
TargetVendor= 0x12d1
**TargetProduct= 0x14c9**
CheckSuccess=20
MessageContent="**55534243123456780000000000000011062000000100000000000000000000**"
```


This way it worked perfectly for me on 11.10.

---

### Post by Steve Kroon on 2011-12-09
> **matteosistisette said:**
> There are two errors in the procedure described by cre8or:



The target product is **14c9**, not 1c05, and the message was missing a "2" between the last 6 and the zeros, that is:

```
5553424312345678000000000000001106**2**000000100000000000000000000
```

Additionally, Mr Buggy VBullettin randomly adds extra spaces here and there, so there was also an extra space, (curiously exactly where the missing 2 was. Coincidence?) 

So the corrected version:




This way it worked perfectly for me on 11.10.

An additional error in cre8or description is that there are closing quotes missing at the end of:

```
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14d1", RUN+="usb_modeswitch '%b/%k'"
```

Thanks for the pointers on the extra spaces - this had me stuck for a while.

Finally, 1c05 and the message cre8or gives work correctly on Lucid - 14c9 does not, since there are no config files for that target.

---

### Post by ryper86 on 2012-05-02
I seem to have no luck with 12.04 LTS and cre8ors method - has anyone experienced similar issues?

Ive formatted and reinstalled 12.04 without any configs and it seems to detect and help you configure the connection according to your network. 

Once you try to connect by clicking 'Vodacom Unrestricted' (my ISP) it says 'Modem Network - Disconnected you are now offline'

lsusb:

12d1:14c9 (without cre8ors nor matteosistisettes changes)

If I change any of the usb-modeswitch config files I get similar if not worse results. In the end the modem was not even being detected - hence the format.

Sakis3g
After running the script and selecting 'Connect 3g' in the selections an error is returned:

'Segmentation Fault (core dumped)'

Seems the forums nor wiki for sakis are loading right now (02/05/12) - hope they return soon!

If anyone has a solution or can help - please oh pretty please!

ryper

---

### Post by alexfish on 2012-05-02
> **ryper86 said:**
> I seem to have no luck with 12.04 LTS and cre8ors method - has anyone experienced similar issues?

Ive formatted and reinstalled 12.04 without any configs and it seems to detect and help you configure the connection according to your network. 

Once you try to connect by clicking 'Vodacom Unrestricted' (my ISP) it says 'Modem Network - Disconnected you are now offline'

lsusb:

12d1:14c9 (without cre8ors nor matteosistisettes changes)

If I change any of the usb-modeswitch config files I get similar if not worse results. In the end the modem was not even being detected - hence the format.

Sakis3g
After running the script and selecting 'Connect 3g' in the selections an error is returned:

'Segmentation Fault (core dumped)'

Seems the forums nor wiki for sakis are loading right now (02/05/12) - hope they return soon!

If anyone has a solution or can help - please oh pretty please!

ryper

can post the results of these commands form the terminal
```
usb-devices
```post only the lines for your devices
```
ls -al /dev/serial/by-id
```

---

### Post by foxy123 on 2012-05-02
I have not tried it on 12.04 but on Oneiric I used the advice from here [http://ubuntuforums.org/showthread.php?t=1893151](http://ubuntuforums.org/showthread.php?t=1893151) when ran into a similar problem.

---

### Post by ryper86 on 2012-05-03
Thanks for the prompt response alexfish, here are the results:

usb-devices:

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14c9 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=Vodafone Mobile Broadband (Huawei)
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=31 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=02 Prot=37 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=33 Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=32 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

ls -al /dev/serial/by-id:

drwxr-xr-x 2 root root 80 May  3 13:29 .
drwxr-xr-x 4 root root 80 May  3 13:29 ..
lrwxrwxrwx 1 root root 13 May  3 13:29 usb-HUAWEI_Vodafone_Mobile_Broadband__Huawei_-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 May  3 13:29 usb-HUAWEI_Vodafone_Mobile_Broadband__Huawei_-if03-port0 -> ../../ttyUSB1

---

### Post by alexfish on 2012-05-03
@ ryper86

the switched mode is not correct > The [COLOR=Blue] Prot=*[/COLOR] are all wrong
need some more info from the terminal
```
sudo gedit /etc/usb_modeswitch.conf
```edit the line
```
DisableSwitching=0
```to
```
DisableSwitching=1
```save
re-plug the device

post the results of lsusb
```
lsusb
```  only post the line relative to your device
and
```
usb-devices
```post the results:
reinstate the line
```
DisableSwitching=0
```save and exit

then will look at further

---

### Post by ryper86 on 2012-05-03
thanks alexfish,

I edited the .conf and set DisableSwitching=1. Saved and exited.

lsusb:

Bus 002 Device 005: ID 12d1:14d1 Huawei Technologies Co., Ltd. 

usb-devices:

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14d1 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=Vodafone Mobile Broadband (Huawei)
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

---

### Post by alexfish on 2012-05-03
need to try try manual switching , disable the the switching in the .conf as before
then from the terminal
```
sudo usb_modeswitch -v 0x12d1 -p 0x14d1 -M "55534243123456780000000000000011062000000100000000000000000000"
```then see what the results are with the "usb-devices" command

---

### Post by ryper86 on 2012-05-03
results of the script:

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 005 on bus 002 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x0f (out) and 0x8f (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: Vodafone
   Model String: CD ROM (Huawei) 
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI
     Product: Vodafone Mobile Broadband (Huawei)
  Serial No.: not provided
-------------------------
Setting up communication with interface 0
Using endpoint 0x0f for message sending ...
Trying to send message 1 to endpoint 0x0f ...
 OK, message successfully sent
Resetting response endpoint 0x8f
Resetting message endpoint 0x0f
 Device is gone, skipping any further commands
-> Run lsusb to note any changes. Bye.

usb-devices:

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14c9 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=Vodafone Mobile Broadband (Huawei)
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=31 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=02 Prot=37 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=33 Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=32 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

---

### Post by alexfish on 2012-05-03
mm!

can try some at commands from the terminal

open up the first terminal
```
cat /dev/ttyUSB0
```open up second terminal

```
echo -e "AT\r" > /dev/ttyUSB0
echo -e "ATZ\r" > /dev/ttyUSB0
echo -e "ATDT*99#\r" > /dev/ttyUSB0
```re-plug the modem
repeat the process in other terminals for /dev/ttyUSB1
open up the first terminal
```
cat /dev/ttyUSB1
```open up second terminal
```
echo -e "AT\r" > /dev/ttyUSB1
echo -e "ATZ\r" > /dev/ttyUSB1
echo -e "ATDT*99#\r" > /dev/ttyUSB1

```if have problem open up the terminal + commands , enter this code first ,
```
sudo su 
```can confirm if can use the commands without "sudo su" command
Post any results:
Added can post the results of this command
```
echo SYSTEM_BIT=$($(which getconf) LONG_BIT)
```

---

### Post by ryper86 on 2012-05-04
seems windows and ubuntu giving 3g hassles...will provide feedback soon

---

### Post by alexfish on 2012-05-06
> **ryper86 said:**
> seems windows and ubuntu giving 3g hassles...will provide feedback soon
Noted from your posts:
```
I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=31 Driver=option = option / modem
I: If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=02 Prot=37 Driver=(none) = cdc_wdm or huawei_ether
I: If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=33 Driver=(none) = diag / diagnostic
I: If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=32 Driver=option = option = un-known Prot value 

```are you sure have post all info from, the usb-devices command

from info this type of modem should have a pcui port , needs this to get info for the and managment

if not showing then possible , the device is faulty . or wrong mode_switch "message" been sent

---

