---
title: "Ir blaster and Directv d12-300"
date: 2009-04-07
forum: Mythbuntu
---

### Post by codymyth on 2009-04-07
I have just recently set up a pvr system using mythbuntu. I have a pvr150 for a tuner and had the remote working by following this guide: [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24). I cannot set up the ir blaster for this part because the bulb at the end fell off. I have purchased a RS232 IR Blaster to use instead of the broken one. 

Now my question is how to set up the IR blaster and get it working with my directv d12-300 stb. i don't know how to do the channel change script or the testing to see of the new ir blaster even works.

p.s. If i can't use the pvr150 remote and RS232 IR Blaster at the same time that is ok because i mostly just want an ir blaster.

---

### Post by azmyth on 2009-04-08
Do a search here, on google and at mythtv.org and you'll find a variety of change channel scripts.

You'll need to have an lircd.conf file for the remote on your settop box. You maybe able to find one lirc web site. I tried this and none worked so I ended up using irrecord and just built a working file.

---

### Post by codymyth on 2009-04-08
would the channel change script be the same as the one for direct control of the stb?

---

### Post by azmyth on 2009-04-08
If you're using an IR Blaster, the change channel script will be the same since all your doing is sending out the channels in IR format. If you want to control the stb, with a hard link I do not know as I didn't set mine up like this.

---

### Post by codymyth on 2009-04-08
whenever i search for a channel change script on Google all i find is channel change scripts for a hard link. So i must find a script different than that hard link script?

Also how do i test if the directv remote i created works?

---

### Post by azmyth on 2009-04-09
```
 #!/bin/sh
REMOTE_NAME = NAME_OF_STB_Remote

for digit in $(echo $1 | sed -e 's/./& /g'); do
  irsend --device=/dev/lircd1 SEND_ONCE SRC-200A_1 $digit
  sleep 0.4  # note, you may have to tweak the interdigit delay up a bit, depending on your DISH receiver model

done

exit 0;

```

Here's the one I use. You can test to see if a signal is sent by using a digital camera. If this works, then the best test is to see if the blaster changes the channel.

---

### Post by codymyth on 2009-04-10
where do i put that at?

---

### Post by codymyth on 2009-04-13
?

---

### Post by azmyth on 2009-04-13
You can put it anywhere. I have mine in /usr/local/bin. Just call it whatever you want like change_ch.sh and chmod 755. You'll then need to add the command to the tuner in myth-setup.

---

### Post by codymyth on 2009-04-15
do i save it as a regular text document?

---

### Post by codymyth on 2009-04-16
Alright so i copyed and pasted your channel change script and saved it as ChannelChange.sh in /usr/local/bin/Channelchange.sh and then linked my imput connection for my tuner card to that exact address and now when i go to watch tv a black screen pops up for a second for to then goes back to the main menu.

I tested my camera to check if it could see ir by pressing remote buttons and i could see little lights, i faced the camera at the ir blaster and tried to click watch tv and i got no flash, what is a way that i can test if the blaster works?

Should my hardware.conf look like this?

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE=""
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""


#Chosen IR Transmitter
TRANSMITTER="DirecTV_RC32"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="/etc/lirc/lircd.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""

---

### Post by codymyth on 2009-04-19
Anyone know?

---

### Post by codymyth on 2009-04-22
Can nobody seriously help me?

---

### Post by codymyth on 2009-05-04
bump

---

### Post by phroman on 2009-05-05
Ok Cody, I'm working up a response, it may be a bit lengthy, so give me a few minutes.  I've just myself come from ir purgatory and still have most of it still in my brain.  Going to get some links together, and files, and will post back within an hour.  Post your:  /etc/lirc/lircd.conf file.  And /usr/share/lirc/remotes/atiusb/lircd.atiusb.conf file.  Exactly which ir blaster did you get?

---

### Post by codymyth on 2009-05-05
The blaster i have is the top blaster on this page [http://www.irblaster.info/](http://www.irblaster.info/) titled RS232 IR Blaster

The file /usr/share/lirc/remotes/atiusb/lircd.atiusb.conf is far to big to post(i don't know how to put it in its own little scrolling thing), and /etc/lirc/lircd.conf is below

/etc/lirc/lircd.conf
#
# this config file was automatically generated
# using lirc-0.8.2(default) on Tue Dec 18 15:27:46 2007
#
# contributed by 
#
# brand:                       DirecTV
# model no. of remote control: RC32
# devices being controlled by this remote:
#

begin remote

  name   DirecTV_RC32
  flags RAW_CODES
  eps            30
  aeps          100

  ptrail        628
  repeat     0     0
  gap    29933

      begin raw_codes

          name enter
             6029    1150    1249    1146     664     534
              663     533    1259     562     624    1144
              663    1131    1251    1145    1262     555
              630

          name up
             6021    1159    1260    1133     647     552
              653     542    1263     533     660     535
              647    1149    1258     537    1260    1129
              650

          name down
             6031    1149    1251    1144     663     535
              663     533    1247     573     629     566
             1238     558    1234    1133     661     561
              636

          name left
             6041    1138    1251    1145     662     535
              663     532    1261     535     650     549
             1255    1136    1253    1140     663    1128
              652

          name right
             6038    1146    1254    1140     651     544
              654     545    1257     536     662    1134
              648     547    1258    1135     647    1147
              660

          name guide
             6042    1141    1264    1129     652     545
              661     538    1260     558    1235     560
              625     573     633     564     639     555
              622

          name menu
             6029    1151    1252    1144     662     535
              663     533    1252     569     628     567
              636     562    1235     560    1230     562
              627

          name back
             6042    1169    1220    1173     632     567
              626     569    1216     580     627    1166
             1216    1178     635     562     616     578
              626

          name exit
             6017    1194    1229    1162     632     566
              636     562    1215     578     629    1167
             1218     575    1225    1171    1232    1157
              631

          name info
             6054    1157    1220    1176     631     564
              627     569    1223     572    1232    1162
             1216     580     624    1169     629    1165
              629

          name ch+
             6027    1156    1248    1145     660     537
              663     533     654     569    1231    1135
              659    1137    1260     560    1238     556
              624

          name ch-
             6024    1157    1259    1132     647     552
              655     543     660     535    1263    1131
             1256     539    1256     539    1260    1130
              649

          name vol+
             6024    1156    1253    1140     665     533
              660    1133     661    1135    1258     562
              632    1137     661     561    1225    1142
              663

          name vol-
             6027    1182    1220    1173     638     558
              623    1173     633    1161    1224     571
              634    1162     622     573    1232    1160
              620

          name mute
             6024    1158    1265    1128     654     544
              661    1133     649    1147    1262     533
              662    1131     657     541    1261    1131
              649

          name previous
             6020    1161    1264    1127     650     551
              656     539     663     536    1257    1134
             1260    1133    1249    1145     662     558
              636

          name 1
             6022    1160    1263    1131     651     546
              659     539     663     533     664     532
              651    1144     663     535     663    1128
              656

          name 2
             6022    1160    1263    1130     650     546
              658     540     660     535     666     561
             1234     531     649     549    1255     535
              666

          name 3
             6020    1164    1263    1130     650     546
              661     537     663     533     667     530
             1254    1140     663     532    1261    1131
              660

          name 4
             6046    1135    1265    1128     655     544
              659     538     663     533     663    1130
              657     541     663     535    1263    1126
              656

          name 5
             6050    1133    1251    1142     663     535
              665     531     649     548     656    1138
              653    1143     662    1131     651     547
              656

          name 6
             6021    1191    1229    1162     629     568
              634     562     618     578     629    1167
             1220     575     622    1173     632    1160
              626

          name 7
             6025    1157    1259    1134     661     537
              663     533     661     535     649    1146
             1261    1133     649    1146    1261     533
              661

          name 8
             6045    1137    1265    1126     658     542
              661     535     660     538    1244     574
              631     566     641    1129    1258     560
              638

          name 9
             6047    1137    1265    1127     656     544
              660     560     638     560    1222     571
              637    1132     650    1146    1262    1129
              651

          name 0
             6029    1152    1258    1135     660     537
              652     547     657    1135     650     549
              654    1139     663    1131    1260     535
              663

          name play
             6045    1166    1227    1167     631     566
              629     567    1215    1179     633     564
              616     580    1222    1171    1225    1167
              626

          name skip+
             6051    1130    1248    1147     658     539
              661     535    1263    1128     658    1138
              651     571     629     569    1236     557
              634

          name skip-
             6047    1140    1258    1135     651     567
              638     560    1220    1173     639     557
             1220    1166     645     560    1222     570
              627

          name pause
             6013    1200    1231    1160     623     575
              631     567    1232    1159     630     568
             1232     564     622     573     625    1169
              623

          name record
             6013    1196    1236    1157     627     571
              634     564    1227    1164     634    1162
              618    1177     637     559    1216    1175
              636

          name stop
             6044    1140    1256    1137     654     544
              656     539    1259    1135     650     568
              638    1135     650     568     636     560
              668

          name red
             6030    1179    1227    1167     625     570
              627    1169     631     567     620     575
              632    1164    1216     578     629     566
              634

          name green
             6017    1191    1232    1160     631     567
              636    1157     629     569     636     562
             1231    1160    1229     566    1237     557
              629

          name yellow
             6013    1194    1236    1157     625     571
              634    1161     621     575     632     566
             1234     561    1230     564     622    1171
              636

          name blue
             6018    1168    1258    1135     647     571
              634    1153     629     556     651    1164
              620     576    1228     568    1234     559
              632

      end raw_codes

end remote

---

### Post by phroman on 2009-05-06
Ok, first, when you're typing a message, at the top of the window are a bunch of icons in the tool bar.  On the right there is one that is a #  If you click on that it will past this:  CODE/CODE into your text area.  You can cut and paste/insert code between these and that's how you get stuff into the scrolling window.  

So, first, is your remote the DirecTV_RC32, and if so does it work?  Look in your /etc/lirc/hardware.conf file.  See how there is one entry for remote and one for transmitter?  You seem to have the remote entered in the transmitter area.  The line: #chosen ir transmitter, is commented out by the # sign, meaning that line is not read by the software at all, it's just there for notes/organization.  But the other lines are actually entered correctly, so it may work. 

```
#Chosen Remote Control
REMOTE=""            giving a unique name of the remote
REMOTE_MODULES=""       what modules to use with this device
REMOTE_DRIVER=""        what drivers to use with this device
REMOTE_DEVICE=""        the specific # lirc uses to id this device
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""     hardware specific location of device

same basics for transmitters

#Chosen IR Transmitter
TRANSMITTER="DirecTV_RC32"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="/etc/lirc/lircd.conf"
TRANSMITTER_LIRCD_ARGS=""
```The line that says:
```
TRANSMITTER_LIRCD_CONF="/etc/lirc/lircd.conf"
```
That tells the program lirc, where to find the file defining all the remote codes to use.  
 

let's start there, is your remote working?

---

### Post by codymyth on 2009-05-06
I have a pvr-150 and the remote worked at one time but then i broke it while trying to get the ir blaster to work, i don't need the remote anymore. That isn't actualy the remote i use to control my directv stb but i have 3 different directv remotes at my house and they all work for this receiver

---

### Post by phroman on 2009-05-07
Ok, I've successfully setup my remote and a usb ir blaster, so I figured, how hard could it be to set up a serial ir blaster?  Well, I just submitted a new post asking for help cause' I can't get mine working...  I'm using different hardware than you are, but I can give you a few things to try out, maybe you'll get lucky. First go to /etc/lirc/ and make a backup of hardware.conf and lircd.conf

At the terminal, type this:   

```
sudo dpkg-reconfigure setserial
```

It will bring up a graphical window a la' 1986, I think the first screen you just hit enter to continue, then the following screen is where you use the arrow key to move down and select :  Manually, then exit out of the window.   What you are doing is telling the lirc program not to overwrite this file in the future, and mess up the manual changes you've made.  

Now you need to modify a file. (these are all just regular text files btw) It's located in  /etc/modprobe.d/lirc - it might be called lirc-serial.conf  You have to un-comment, ie. remove the hash mark, so that the program reads the line.  It should look like this: 

```
#COM1 equivalent , /dev/ttyS0
options lirc_serial irq=4 io=0x3f8
#COM1 equivalent , /dev/ttyS2
#options lirc_serial irq=3 io=0x2f8
```


Another file to edit, it's located in /var/lib/setserial/autoserial.conf   You're going to add or modify if it's already there, a line at the bottom:   
```
/dev/ttyS0 uart none
```
Then, you are going to add that exact line again into another file, located at:   /etc/serial.conf   If the file doesn't exist, create it.    

2:  Back to the command line, type: dpkg-reconfigure lirc

The first screen/section is for setting up a remote, use the arrows key to move up to NONE, hit enter.  This next section is where lirc will create a hardware.conf file for you, based on what you choose.  You want to move down to where it says, SERIAL, I think there is a choice of SERIAL IR of some sort, and one for SERIAL (UART) Direct TV Receiver.  Try the ir one first. Next screen you should choose ttyS0,  and  exit out of the program.  Next is to open your /etc/lirc/hardware.conf file.  This is what lirc just created, see in the transmitter section where it says:
 
```
#Chosen Transmitter
TRANSMITTER=" what ever the name is here "
```
change the name in quotes to "SERIAL"

Next, go to the file: /usr/share/lirc/transmitters/directtv/general.conf  About 10 lines down or so it will say:  name .
enter SERIAL here, no quotes or anything.  Save this file.

Back to the command line:  Enter this:  
```
sudo irsend -d /dev/lircd0 SEND_ONCE SERIAL guide
```
This is where we try to tell the program lirc to send the code for guide, (the direct tv guide) to the STB.  Copy any errors that you see if this doesn't work, ie. if it doesn't bring up your Direct TV guide.  But, hopefully your Direct TV Guide came up.  If not, post back and hopefully I've learned more and can help debug.

---

### Post by codymyth on 2009-05-11
i got this after running the irsend code:
```
cody@cody-myth:~$ sudo irsend -d /dev/lircd0 SEND_ONCE SERIAL guide
irsend: could not connect to socket
irsend: No Such file or directory
```

I did not have /etc/modprobe.d/lirc or /etc/modprobe.d/lirc-serial

---

### Post by phroman on 2009-05-12
I came across this post a while ago, it may give you some help:

[http://ubuntuforums.org/showthread.php?t=789608]("http://ubuntuforums.org/showthread.php?t=789608")

I think it's someone using a similar hardware setup as you are.  The second page is the meat of it.  I'm in serial blaster hell myself right now, let me know what you come up with.

---

### Post by codymyth on 2009-05-12
well i think one of my problems is that i do not have a /etc/modprobe.d/lirc file

---

### Post by phroman on 2009-05-12
I'm not sure how that's possible if you have lirc installed...
Didn't you get your remote working with lirc?

---

### Post by codymyth on 2009-05-12
well my computer froze during a upgrade to 9.4 (was trying to fix a sound problem) so i had to fresh install mythbuntu 8.10

Do i need to make my own channel change script for that to work?

---

### Post by phroman on 2009-05-13
I've seen this one referred to quit a bit by others.  

[http://home.eng.iastate.edu/~superm1/contrib/change-channel-lirc.pl](http://home.eng.iastate.edu/~superm1/contrib/change-channel-lirc.pl)

There are a few tweaks you'll probably need to make to it.  Here's two posts that might help you, I think down around post #5 of the first one:

[http://ubuntuforums.org/showthread.php?t=789608](http://ubuntuforums.org/showthread.php?t=789608)

[http://ubuntuforums.org/showthread.php?t=742672&page=2](http://ubuntuforums.org/showthread.php?t=742672&page=2)

---

### Post by elgordo123 on 2009-05-13
Can you guys try my suggestion from here?  It worked perfectly for me. 

[http://ubuntuforums.org/showthread.php?t=1136391&highlight=knoppmyth](http://ubuntuforums.org/showthread.php?t=1136391&highlight=knoppmyth)

---

### Post by codymyth on 2009-05-13
great news!! I got mine to work. i tried  doing what elgordo123 said but on the install it said press any button and when i pressed a button nothing happened. So I went back to the code phroman gave me because I thought that i might just be trying to use the wrong lirc dev so i did a "ls -l /dev/lirc*" and it had 2 options: lirc0, lircd. and to my suprise when i used lircd my guide came up! I don't know if that will help you at all with yours phroman but i would suggest trying all the lirc devices listed on "ls -l /dev/lirc*". 

Thank You for all your help phroman and all others who helped.

---

### Post by elgordo123 on 2009-05-14
Glad you got it working.   However, the install doesn't not say anything about "Press a button..",  however it does say "Press a key to continue.."   <-- Press any key on the keyboard (not the remote)!   That is probably why it didn't do anything.  ;)

---

### Post by phroman on 2009-05-14
Awsome!  I'm glad you got it working.  I've just recruited a friend of mine to help me out with set top box control.  We're working on a setup to put an end to all of this ir blaster stuff, and integrate set top box control seamlessly into Myth TV.  I'll definitely keep updates posted here on the forums.  ):P

---

### Post by codymyth on 2009-05-14
thats great phroman! theres alot of trouble caused by those stb.

no elgordo123 i don't have my remote set up, i was using my keyboard.

---

### Post by samymusleh on 2010-03-30
Hi there Phroman, I am a Newbie in Ubuntu, I will like to know if u could help me... I read your post and I like it... 
 
So let me explain myself to see if u or other people in the forum could help me, I have install Ubuntu 9.10 with Mythtv Backend on a computer, and 3 frontend in diferents computers, I have 3 Hauppauge Wintv-hvr-1950 install in the backend connected to 3 Direct Tv d12-100 Receivers.
 
In the frontends I have install a Streamzap Pc Remote, Usb Infrared Receiver, I could control the Mythtv interface, I could play, pause, stop, rewind, etc.. What I cant do is change channels on mythtv watch tv... 
 
Some post that I have read before is that the Ir Blaster has to be installed and the changing channels script has to be in the **/usr/bin **folder. But I cannot get this 2 things...
 
Plz Help me I cant get it to work...
Thanks a lot....
 
> **phroman said:**
> Ok, I've successfully setup my remote and a usb ir blaster, so I figured, how hard could it be to set up a serial ir blaster? Well, I just submitted a new post asking for help cause' I can't get mine working... I'm using different hardware than you are, but I can give you a few things to try out, maybe you'll get lucky. First go to /etc/lirc/ and make a backup of hardware.conf and lircd.conf
 
At the terminal, type this: 
 
```
sudo dpkg-reconfigure setserial
```
 
It will bring up a graphical window a la' 1986, I think the first screen you just hit enter to continue, then the following screen is where you use the arrow key to move down and select : Manually, then exit out of the window. What you are doing is telling the lirc program not to overwrite this file in the future, and mess up the manual changes you've made. 
 
Now you need to modify a file. (these are all just regular text files btw) It's located in /etc/modprobe.d/lirc - it might be called lirc-serial.conf You have to un-comment, ie. remove the hash mark, so that the program reads the line. It should look like this: 
 
```
#COM1 equivalent , /dev/ttyS0
options lirc_serial irq=4 io=0x3f8
#COM1 equivalent , /dev/ttyS2
#options lirc_serial irq=3 io=0x2f8
```
 
 
Another file to edit, it's located in /var/lib/setserial/autoserial.conf You're going to add or modify if it's already there, a line at the bottom: 
```
/dev/ttyS0 uart none
```
Then, you are going to add that exact line again into another file, located at: /etc/serial.conf If the file doesn't exist, create it. 
 
2: Back to the command line, type: dpkg-reconfigure lirc
 
The first screen/section is for setting up a remote, use the arrows key to move up to NONE, hit enter. This next section is where lirc will create a hardware.conf file for you, based on what you choose. You want to move down to where it says, SERIAL, I think there is a choice of SERIAL IR of some sort, and one for SERIAL (UART) Direct TV Receiver. Try the ir one first. Next screen you should choose ttyS0, and exit out of the program. Next is to open your /etc/lirc/hardware.conf file. This is what lirc just created, see in the transmitter section where it says:
 
```
#Chosen Transmitter
TRANSMITTER=" what ever the name is here "
```
change the name in quotes to "SERIAL"
 
Next, go to the file: /usr/share/lirc/transmitters/directtv/general.conf About 10 lines down or so it will say: name .
enter SERIAL here, no quotes or anything. Save this file.
 
Back to the command line: Enter this: 
```
sudo irsend -d /dev/lircd0 SEND_ONCE SERIAL guide
```
This is where we try to tell the program lirc to send the code for guide, (the direct tv guide) to the STB. Copy any errors that you see if this doesn't work, ie. if it doesn't bring up your Direct TV guide. But, hopefully your Direct TV Guide came up. If not, post back and hopefully I've learned more and can help debug.

---

### Post by phroman on 2010-03-30
Hi samymusleh, I've never setup a system with a remote backend so I'm not sure myself how channel changing works with multiple frontends and multiple tuner cards.  I'm guessing its similar to a set up on a local machine, so I'll give it a go.  

You have the streamzap remote working, so that's obviously good, but now you need to set up transmitting.  I had a lot of trouble with lirc and infrared transmitting when I was trying it last time simply due to my inexperience.  I now have my system set up with a serial transmitter, not infrared, and I think it's much easier to setup, and from everything I've read, more reliable.  This does requires that you have a com port on your system, and then you have to buy 2 cables.  Together the cables will probably cost you about $26.00.  So before we go any further, let me know if this is ok with you, then we'll get to the setup. Phroman.

---

