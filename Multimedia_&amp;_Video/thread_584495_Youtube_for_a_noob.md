---
title: "Youtube for a noob"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by d-_-b on 2007-10-21
yeah i know it rhymes lol...

anyways, i recently jumped on the linux bandwagon from vista/windows and so far i am pleasantly delighted. should have made this transition ages ago. :)

now down to my question. i watch a lot of youtube videos, but whenever i go to watch ANY video on youtube, i get this message (error?) instead of the video - "Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player."
i dont know what to do. actually, on a previous install of ubuntu gutsy, i installed the missing plugins that firefox tells you to do. however, first i couldnt install the adobe flash since it said something about already being installed. so i resorted to installing the gnash, although this solved the issue by actually playing the video, the rewind/FF/volume/play/pause pane just below the video is all messed up and i cant even rewind or FF without firefox freezing up on me.

so heres my ultimate question, what are the exact steps i have to take in order to 1) play the youtube videos and 2) not screw up the video pane? please describe to me in common layman terms since im a recent linux convert and im relatively behind on linux terminology. (btw, did i mention i am a COMPLETE linux noob? ... lol)

Thank you everyone. I will be around this forum much more often now, not only with questions but hopefully with solutions to other ppls questions as well. :)

---

### Post by d-_-b on 2007-10-21
can anybody help me? :(

---

### Post by peebly on 2007-10-21
Hello

Using the terminal which is under applications - accessories type the following commands.

sudo apt-get install sun-java6-plugin

sudo apt-get install flashplugin-nonfree

you will have to input your password after the first command.

---

### Post by d-_-b on 2007-10-21
> **peebly said:**
> Hello

Using the terminal which is under applications - accessories type the following commands.

sudo apt-get install sun-java6-plugin

sudo apt-get install flashplugin-nonfree

you will have to input your password after the first command.

does this apply to kubuntu too? i just changed from ubuntu to kubuntu becuz i like the look of kde better than gnome =P. thanks for your response btw:)

---

### Post by peebly on 2007-10-21
> **d-_-b said:**
> does this apply to kubuntu too? i just changed from ubuntu to kubuntu becuz i like the look of kde better than gnome =P. thanks for your response btw:)

I have to say, I don't really know as I have never used Kubuntu or a KDE desktop.

But you could try it in the terminal, if its called that in Kubuntu.

---

### Post by d-_-b on 2007-10-21
> **peebly said:**
> I have to say, I don't really know as I have never used Kubuntu or a KDE desktop.

But you could try it in the terminal, if its called that in Kubuntu.

still, thanks a lot for ur response. it did give me insight on how to approach the problem :)
can a kubuntu user confirm that the command lines kindly given by peebly above is how i should approach the youtube problem? basically how would i play youtube on firefox in kubuntu is what im asking... lol 
thanks again :)

---

### Post by SeePU on 2007-10-21
d-_-b, yes, you can try the command line if you want.   I used synaptic and I use Kubuntu 7.10.   I can view YouTube videos just fine.  When it's not working, it usually has something to do with plugins.  

You can also download the videos with firefox extensions (add-ons).

---

### Post by oldcity on 2007-12-10
i too get the message (error?) instead of the video - "Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player."

I followed the advise from peebly in item # 3 see below.

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Hello

Using the terminal which is under applications - accessories type the following commands.

sudo apt-get install sun-java6-plugin

sudo apt-get install flashplugin-nonfree

you will have to input your password after the first command.
__________________
Registered Ubuntu User 18039 Everyday's a school day 
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

$sudo apt-get install sun-java6-plugin

It showed some install stuff, then

Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-bin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;  
 &#9474;     form, any other machine readable materials including, but not         &#9618;  
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
Process interupted after about 15 minutes

System message advised to do the following.
$sudo dpkg --configure -a

Then did
$sudo apt-get install flashplugin-nonfree

System message advised to do the following.
$sudo apt-get -f install

Got a similar screen (Package configuration) Never finished to give the <OK>.
Interupted after more than 1 hour. Doesn't appear to have completed.

What now.

tia
oldcity

---

### Post by ron999 on 2007-12-10
@oldcity
The install has paused until you accept the license conditions.
You'll probably have to hit 'enter' or 'space bar' to continue.

---

### Post by oldcity on 2007-12-10
Ron999 tried that got no where.

Got a new DVD in mail today and tried it. It played video but no
sound. Along the way it told me that I had to install some codecs
It went to a box to install them. After clicking it told me to 
sudo dpkg --configure -a
I was then able to complete the install. I think it was glstreamer.
I now have sound with the dvd and I can now listen to commercial
radio stations.
Thats my success story
hth
oldcity

---

