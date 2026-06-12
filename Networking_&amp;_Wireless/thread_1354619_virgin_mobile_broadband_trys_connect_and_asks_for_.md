---
title: "virgin mobile broadband trys connect and asks for network password"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by mjneil.81 on 2009-12-14
hello,

i'm having trouble with my virgin mobile broadband(e160e). I have tried the following suggestions from the forum:
change virgininternet to VirginBroadband, remove # from -chap and entered in username and password. 
when i try to connect to the internet i get a prompt asking me for a network password. 

if anyone could help out it would be greatly appreciated as i am an absolute beginner with linux.

thank you in advance.

---

### Post by alexfish on 2009-12-14
removed

---

### Post by mjneil.81 on 2009-12-14
hey alexfish,

i have provided some screenshots. the one titled screenshot.png is the prompt asking for the password. and the others are of the settings that i have been trying to use. 

thanks for the tips with the shots and uploading.

---

### Post by mjneil.81 on 2009-12-14
and the one i left behind......

---

### Post by alexfish on 2009-12-14
Hi  Back Now

We will take this step by step First We will Identify the device

1 : follow the sequence of the screen shots bellow

2 : from the terminal type or copy this command



Code:

lsusb

Your output will look something like mine/ Hopefully

alex@alex-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Navy]Bus 001 Device 057: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
alex@alex-desktop:~$

---

### Post by mjneil.81 on 2009-12-14
sorry it has taken so long to get back to you. it was getting late.
i have taken the screenshot of lsusb command results. 
 
on my sytem the disk utility is missing the other screenshot shows the drop down menu.

---

### Post by mjneil.81 on 2009-12-14
screenshots

---

### Post by alexfish on 2009-12-15
Hi 

System on blink yesterday

need to know/ " pay plan " /you have with /virgin

 the /phone number/ relates to the /pay plan/

leave the details as they are in the first  screen shot

then check or uncheck the the boxes in the second shot to get best performance of gsm

try one at a time

---

### Post by mjneil.81 on 2009-12-16
alexfish, 

i'm on a post paid plan i'm not 100% sure what you meant in your post cause of all the "/" but i tried the details that are shown in the screenshot and tried combinations of and 1 at a time of the CHAP, PAP, etc...

---

### Post by alexfish on 2009-12-16
> **mjneil.81 said:**
> alexfish, 

i'm on a post paid plan i'm not 100% sure what you meant in your post cause of all the "/" but i tried the details that are shown in the screenshot and tried combinations of and 1 at a time of the CHAP, PAP, etc...

[SIZE=2][B]Need to Know If you are on contract or Pay by voucher etc
[/B][/SIZE] 
Will post details shortly Problems with server !

on going update

Please Wait @

The entry NEXT PAGE Not Complete

---

### Post by alexfish on 2009-12-16
[COLOR=DimGray][FONT=Verdana, Arial][B]UK ONLY
If you are on contract see here   / The default settings are in the screen shot 

GPRS WAP settings:[/B][/FONT]
[/COLOR] 
                                                      [COLOR=SlateGray][FONT=Verdana, Arial][SIZE=2]**Homepage:                 **[http://www.virgin.com/mobile/wap/](http://www.virgin.com/mobile/wap/)[B]
Access Point                 (contract): [/B]goto.virginmobile.uk[B]
Gateway (IP) address :                 [/B]193.30.166.003[B]
Port number: [/B]8080[B]
Username:                 [/B]user[B]
Password: [/B](leave blank)[B]
Session type:                 [/B]Continuous / permanent[B]
Authentication: [/B]Normal[/SIZE][/FONT][/COLOR]

---

### Post by alexfish on 2009-12-16
[SIZE=3][COLOR=Blue]Re :Australia Virgin Mobile  Gprs 
[/COLOR][/SIZE]

---

### Post by mjneil.81 on 2009-12-17
alexfish

i tried the suggested settings. still no success. might have to
give it a miss for a while, i'm running low on time at the moment thanks for your time and assistance.

i'll give it another go in a couple of weeks.

---

### Post by mjneil.81 on 2010-01-05
i finally figured out how to connect the internet with virgin mobile broadband using ubuntu 9.04 in australia
i will outline the steps that were successful for me:

the screenshots attached below are provided to help with the following instuctions

look at 1(terminal).png 
open terminal and type what follows after the $ symbol ( note: be aware that the spaces are neccessary) press enter

you will be prompted for your password. see 2(terminal).png type your password to gain root privaliges, press enter

you will see a window as shown in 3(gedit).png
note the position of the cursor in the line that says " #-chap" scroll down to this line. and
remove the hash symbol ( # ) so it looks like the next screenshot shown in 4(gedit).png
save the changes by file> save. close window.

next go to system > preference > network connections and go to the mobile broadband tab highlight virgin mobile and select edit you will get a window as shown in 5(Editing Virgin Mobile).png
type " blank" in both the username and password fields and change the APN field to "VirginBroadband" 
next go to the PPP Setting tab and select configure methods.... button and deselect CHAP as shown in 6(Editing PPP).png

i hope that this helps anyone who has been having the same trouble that i was having.

---

### Post by mjneil.81 on 2010-01-05
and the last screen shot...

---

### Post by loopy69 on 2010-01-06
Thanks for this info, I got virgin mobile broadband up and running for a friend in about 5 minutes with this information...

Thanks
Brett

---

### Post by pdc on 2010-01-07
good work; well done; I think it is only Virgin Australia that needs to disable chap; I cannot find the same for the UK Virgin; and from the description, one needs to edit the file /ect/ppp/options as well as edit the graphical interface of network manager

---

### Post by mjneil.81 on 2010-01-08
glad the info helped out!!!
i'm not 100% sure if both "/ect/ppp/options"and graphical interface  network manager have to be edited but i think disabling CHAP by editing "/ect/ppp/options" stops the problem that some people were having with the CHAP tick box under network manager reverting back to being marked every time they restart, log out etc.

---

### Post by prule on 2010-01-21
I found these comments essential to get my Huawei e160e Virgin mobile broadband working on ubuntu 9.10.

I documented my results here : [http://www.javathinking.com/2010/01/ubuntu-virgin-mobile-internet-pre-paid-and-the-huawei-e160e/](http://www.javathinking.com/2010/01/ubuntu-virgin-mobile-internet-pre-paid-and-the-huawei-e160e/)

How though, do we get another plan into the network connections manager? i.e. There is a default plan using the APN 'VirginInternet' which can I assume is for post paid customers. Is it possible to add another plan into the ubuntu distro for the APN 'VirginBroadband' which I assume is for pre-paid?

---

### Post by mjneil.81 on 2010-01-22
my plan with virgin is post-paid, the info for the authentication, password and the APN was taken from the virgin (Au) website found at the address below.

 [http://virginmobile.custhelp.com/app/answers/detail/a_id/57/~/supported-usb-mobile-broadband-modems]("http://virginmobile.custhelp.com/app/answers/detail/a_id/57/%7E/supported-usb-mobile-broadband-modems") 

hope this helps a little.

---

### Post by pdc on 2010-01-22
Hi mjneil.81; I thought you did great work detailing how to configure a Virgin Oz; great to have it available; 

I think when prule said 

> How though, do we get another plan into the network connections manager?

he may have meant creating a default entry for Virgin Australia pre-paid, so it comes up as an option in network manager

if one google searches on 

> gnome network manager apn settings update

one gets various interesting posts, one of which is

[http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders](http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders)

if you want to look at this topic prule, and see if you can update the Virgin Oz settings, as I have seen this more than once

and of course there are others

[http://blogs.gnome.org/dcbw/2009/06/22/mobile-broadband-assistant-makes-it-easy/](http://blogs.gnome.org/dcbw/2009/06/22/mobile-broadband-assistant-makes-it-easy/)

seems like the above post just wants you to file a bug report

[https://bugzilla.gnome.org/enter_bug.cgi?product=NetworkManager](https://bugzilla.gnome.org/enter_bug.cgi?product=NetworkManager)

seems pretty straightforward

---

### Post by ripty on 2010-01-28
> **mjneil.81 said:**
> i finally figured out how to connect the internet with virgin mobile broadband using ubuntu 9.04 in australia
i will outline the steps that were successful for me:
 
the screenshots attached below are provided to help with the following instuctions
 
look at 1(terminal).png 
open terminal and type what follows after the $ symbol ( note: be aware that the spaces are neccessary) press enter
 
you will be prompted for your password. see 2(terminal).png type your password to gain root privaliges, press enter
 
you will see a window as shown in 3(gedit).png
note the position of the cursor in the line that says " #-chap" scroll down to this line. and
remove the hash symbol ( # ) so it looks like the next screenshot shown in 4(gedit).png
save the changes by file> save. close window.
 
next go to system > preference > network connections and go to the mobile broadband tab highlight virgin mobile and select edit you will get a window as shown in 5(Editing Virgin Mobile).png
type " blank" in both the username and password fields and change the APN field to "VirginBroadband" 
next go to the PPP Setting tab and select configure methods.... button and deselect CHAP as shown in 6(Editing PPP).png
 
i hope that this helps anyone who has been having the same trouble that i was having.
 
NICE!!! after 2 hours + of searching the threads i now have my virgin mobile BB up and running on ubuntu 9.10! (Im a n00b to the bunt's obviously)
Cheers MJ, the screen grabs worked a treat. ive been banging my head against the ubuntu brick wall for days and after joining this site the fix was so simple. wish i could buy you all a beer or 20!!!
Finally I can get rid of the stanky Gates MS OS
So stoked!!!
thanks to all and ubuntuforums.org

---

### Post by kyteflyer on 2010-03-21
Not working for me.  Makes NO sense.  I've been given three different methods for dealing with this and none are working.  I am probably going to revert to windoze.  dang!!

[edit]  I went back to the linux section in whirlpool,net.au and found that a reply had been made.  He asked if my user permissions allowed me to connect with a modem and when checked... nope.  One tiny piece of information which if I had known it, would have solved my issues yesterday.  Why in gods name is this not checked on by default???? GAWD!!

So,now everything is fine.  Didnt need to install wvdial, didnt need to edit configs, just needed that.  crikey!

---

### Post by kohlercharles on 2010-05-28
mjneil.81 - Thank you so much for posting such plain and simple instructions!  My 3g is working great on 10.04 netbook remix.

---

### Post by TheNorthernSurvivalist on 2011-02-06
Well guys, I was using Verizon mobile broadband and in Ubuntu it hooked up immediately. However I am switching to prepaid, either ATT or Virgin Mobile. 

When I first had Verizon I was set up with Winblows Vista. Not sure if had anything to do with it.

---

### Post by shane wiley on 2011-03-06
I have spent hours trying to get my son's virgin mobile broadband to work, and thanks to contributions by the following post I got it working.
Before you read it tho just my $0.02c
When doing system > preference > network connection make sure you 'apply' each tab or things will go back to what they were before.
And if it is prepaid, as mine was, it seemed to need the different APN, which I think was virgin broadband, not virgin internet (my son has run off with the computer to his new home so  I can't check)
And also, possibly, all the first stuff about terminal, disabling the hash line for chap etc etc MAY NOT be necessary, as the network connect applet is likely to do that.

I hope no one has to go over all the stuff and reading I had to do,a lot of it dreaming by good intentioned people.  Ubuntu needs a 'golden' manual, where things that really work are put together in a easy to read format by the administrator.
Well here is the one that worked for me. The poster included thumbnail screen shots for all, if you need them you will have to search, but try without them by going to the paragraph that starts with **....
And by the way, a password box the the Huewai came up (very frustrating, I tried every known system password) but in the end when things were done as below it did not seem to need it.  If it still does, type in "blank" as this is what you have now set it to.

Originally Posted by mjneil.81  
i finally figured out how to connect the internet with virgin mobile broadband using ubuntu 9.04 in australia
i will outline the steps that were successful for me:

the screenshots attached below are provided to help with the following instuctions

look at 1(terminal).png 
open terminal and type what follows after the $ symbol ( note: be aware that the spaces are neccessary) press enter

you will be prompted for your password. see 2(terminal).png type your password to gain root privaliges, press enter

you will see a window as shown in 3(gedit).png
note the position of the cursor in the line that says " #-chap" scroll down to this line. and
remove the hash symbol ( # ) so it looks like the next screenshot shown in 4(gedit).png
save the changes by file> save. close window.

** next go to system > preference > network connections and go to the mobile broadband tab highlight virgin mobile and select edit you will get a window as shown in 5(Editing Virgin Mobile).png
type " blank" in both the username and password fields and change the APN field to "VirginBroadband" 
next go to the PPP Setting tab and select configure methods.... button and deselect CHAP as shown in 6(Editing PPP).png

i hope that this helps anyone who has been having the same trouble that i was having

---

### Post by bjorn.aigen on 2011-08-15
Minimal settings for a successful setup.

Country: Australia
City: Brisbane, Queensland
Plan: Prepaid Virgin Mobile Broadband 
Purchase date: 12/08/2011
Cost: $49.00AUD for 1 month
Device: Huawei E160E HSDPA USB stick
OS: Ubuntu 10.10 Maverick Meerkat
 
Key Mobile Broadband settings:
APN: VirginBroadband
Username: [blank]
Password: [blank]
PPP Authentication: PAP

Principle steps when configuring in Network Connection Manager:
1. Choose "Mobile Broadband" as APN
2. Remove all PPP Authentication methods except PAP

Note: I did not need to use a terminal nor did I modify the /etc/ppp/options file.

---

### Post by pdc on 2011-08-15
well done; enjoy

I guess these screenshots describe your settings

---

### Post by bjorn.aigen on 2012-10-03
[pdc:]("http://ubuntuforums.org/member.php?u=18016")  Yes, the screenshots are a correct and complete representation of the solution.

---

