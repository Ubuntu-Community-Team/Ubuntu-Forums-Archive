---
title: "Ardour - Jack- USB soundcard problems"
date: 2009-07-12
forum: Multimedia Software
---

### Post by aierlan on 2009-07-12
**Ardour - Jack- USB soundcard problems** 			
 			 			 		   		 		 		Hi, 

I've been using Ubuntu 9.04 for about 2 weeks now. 
I have an external USB sound card (Tascam US - 122) which I want to use to record Audio in Ardour. 
I'm having trouble getting any audio signal into ardour   

I've installed Jack and run it first but I'm really not sure of the configurations. I can only start jack if I deselect "realtime" in the setup menu or esle it wont run. 

And when I open up ardour I get an error message from Ardour saying "Error - no devices found for driver "netjack".

I'm absolutley clueless as to how to get Ardour to work with Jack. 

I'm also trying to set my soundcard as the default device for firefox and cant figure it out either. 

I'd appreciate any advice in beginners language 

Thanks in advance for any help!

---

### Post by aierlan on 2009-07-12
[SIZE=2]I've got Jack running now but still can't get any audio signal in ardour.

In system - preferences - sound I've set all my preferences to my tascam soundcard (alsa).   Is this right?

Then I can run jack.  
In Jack setup menu I've selected /usr/bin/jackd as the server path.  
Driver is alsa.
Parameters I've selected:
monitor
Priority - defaul
Frames/Period 1024
Periods/Buffer: 2
Interface: hw:0 (Inte ICH5) - If I select hw:1 (my tascam soundcard) JACK crashes saying: [/SIZE]

p, li { white-space: pre-wrap; }  [SIZE=1]Could not connect to JACK server as client.[/SIZE]
 [SIZE=1]- Overall operation failed.[/SIZE]
 [SIZE=1]- Unable to connect to server.[/SIZE]
 [SIZE=1]Please check the messages window for more info[/SIZE]


[SIZE=1][SIZE=2]Everything else is set to default[/SIZE]
[/SIZE]

**[SIZE=1][SIZE=2]Does anyone have any idea if the above settings are correct?[/SIZE][/SIZE]**


[SIZE=2]So I run Jack and then open up ardour, 
[/SIZE]


[SIZE=2]Audio Set up  in Ardour:[/SIZE]
[SIZE=2]Device: Driver - Alsa 
[/SIZE]
[SIZE=2]Interface - Should I select Tascam here or INTEL ICH5????? Neither seem to make a difference when i go to record. 
[/SIZE]
[SIZE=2]In the 'advanced' or audio setup  the input and output device is selcted as Intel ICH5.  I don't have any option to change these. Is this the root of my problem. 
[/SIZE]
[SIZE=2]**So now Jack is running, so is ardour without any error messages but I still can't get any audio signal in.**[/SIZE]


 [SIZE=2]Anyone who can please help as this is driving me absolutley nuts.  I'm an experienced Cubase and reason user but am completly lost when it comes to this.  I can't seem to find a fix for this problem in any forums.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]
[/SIZE]

---

### Post by aierlan on 2009-07-13
Figured it out,. everything's working fine now

---

### Post by Shininggg on 2009-08-07
dude you gotta explain, because i'm clueless here i got my presonus card and i have to log in damn winXp each time i want to record stuff..

---

### Post by vinithepooh on 2009-08-16
I have the same problem aierlan had.

I can only start jackd if I set the soundcard to the built-in card
on my laptop (hw:0). 
I have a Lexicon audio interface (hw:1),
but when I set the soundcard in the qjackctl set-up to hw:1,
jackd cannot be started.

I get the same error messages as those in aierlan's first posting.

I wonder how the problem was fixed?

Thanks in advance for any help!

---

### Post by GhostofJohnToad on 2009-08-18
Well, I am having a similar problem with my Tascam US122 as well.  It is listed as hw:1.  If i use my onboard soundcard hw:0, Jack and Ardour start up and work fine.  If I select hw:1 Jack starts but when I start Ardour it tries to start and then gives me a memlock error and then both Jack and Ardour exit.  

I found that if I start qjackctl with ```
gksudo qjackctl
``` both hw:0 and hw:1 work fine.  It appears the permissions for the usb device are not set correctly.

---

### Post by Shininggg on 2009-10-09
> **GhostofJohnToad said:**
> Well, I am having a similar problem with my Tascam US122 as well.  It is listed as hw:1.  If i use my onboard soundcard hw:0, Jack and Ardour start up and work fine.  If I select hw:1 Jack starts but when I start Ardour it tries to start and then gives me a memlock error and then both Jack and Ardour exit.  

I found that if I start qjackctl with ```
gksudo qjackctl
``` both hw:0 and hw:1 work fine.  It appears the permissions for the usb device are not set correctly.

That might be it i'll try thst at home later and give some feedback

---

### Post by markbuntu on 2009-10-09
Tascam US 122
If you have a Tascam US122 you also need a firmware loader:

[http://ubuntuforums.org/showpost.php?p=6272809&postcount=3](http://ubuntuforums.org/showpost.php?p=6272809&postcount=3)

---

