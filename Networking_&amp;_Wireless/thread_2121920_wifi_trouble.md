---
title: "wifi trouble"
date: 2013-03-03
forum: Networking &amp; Wireless
---

### Post by eyeneedhelp on 2013-03-03
new here on Sunday. using ubuntu 12.4. getting familiar and like it. looking to get out of windows.
using a usb wifi adapter,cant stay connected to a net. my windows laptop next room connects fine.
ubuntu was ok the first day i used it,now not staying connected. help?

using the windows lpt now for this

---

### Post by eyeneedhelp on 2013-03-03
i'm new here but not new to computing. its easy to see that the wifi problem is not new to ubuntu.
i had hope of leaving windows but i dont want a new technical saga adventure like we had in the early days of win/io/interupts
etc,etc. so i wont hold out much hope!!

---

### Post by QIII on 2013-03-03
Wifi issues affect the broader Linux ecosystem, not just Ubuntu.

Unfortunately, until OEMs make Linux drivers for their hardware more common we will continue to have to struggle and find work-arounds.

It is not a wise business decision for many OEMs to expend the resources to maintain drivers that work for such a small segment of the market, so they concentrate on Windows.  I don't blame them.

---

### Post by kurt18947 on 2013-03-03
A good first step would be to report the output from one or both these commands.  If your wifi adapter is internal, type this in a terminal:

```
lspci
```

If it's a USB 'dongle', type this:

```
lsusb
```

What we're looking for is something like this:

```
:~$ lsusb
**Bus 001 Device 002: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]**
Bus 003 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 004: ID 047d:2048 Kensington 
Bus 009 Device 002: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 04f9:01f3 Brother Industries, Ltd 

```

There are families of devices that have similar characteristics and similar fixes.  The actual manufacturer of the device isn't that relevant, what's relevant is the make and model of the chipset in the device.

---

### Post by eyeneedhelp on 2013-03-03
can i assume that there actually is a usb device that wsill work with linux,WITHOUT a hassle?
i have had my years of struggle/hard wiring  and i just want to pnp!

---

### Post by Hadaka on 2013-03-03
Hi, to answer your question...YES there are....hassel free.
here is mine.
Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
rt73 usb driver, already in the kernel.
its old,expensive, has an antenna so huge it could probably talk to alien spacecraft
the body is so big and runs so hot, I rest my cup on it to keep my coffee warm.
It has run error free....3 years...plug and play..unubtu 11.10  12.04  12.10
so plug yours in,open a terminal  ctrl/alt/t and post the results of..

```
lsusb | grep -v root 
```

and see if we can get it working for you.

thanks.

---

### Post by eyeneedhelp on 2013-03-04
sorry,i could'nt make use of the last post,item??
i took another chance,ordered asus usb n13, claims ubuntu function.
report back later

---

### Post by eyeneedhelp on 2013-03-04
sorry for confusion. in my newness i failed to mention my original usb wifi,"widemac'. it worked/works sometime briefly.
i ordered a new asus and im looking for drivers for the widemac.
im new,struggling! i am Not knowledgable in linux,learning slowly

---

### Post by eyeneedhelp on 2013-03-05
The plot thickens!
the seller uploaded a zip file with the driver disc data that i lost,my dvd "ate" the disc.
i copied the zip file to a folder on my win 7 comp.and also extracted the file to that folder. then copied both to a thumb drive,to my ubuntu comp.no matter what i try on ubuntu i get errors.
so,back to win 7 comp. i disable the internal wifi and run the realtek driver for win 7,THIS COMP,and i am now connected with the widemac/realtek usb wifi on win 7 so i know it works!!,but alas not on ubuntu??

i tried extracting on the ubunto comp but get errors when i run it??
so im lost again

---

### Post by eyeneedhelp on 2013-03-05
So i guess im in the same boat as many others, no answers,and i  was very much looking to use ubuntu.
im using my usb wifi adapter on my win 7 comp as a very sucessful test. i think its better than the built in wifi in my laptop.
i installed the win driver and it works as you can see. (im on win 7 now)
i cannot get the ubuntu driver to setup. in fact cant find setup. when i extract the driver package on my linux comp and try anything i get errors that i dont understand.
the usb unit connects without the drivers but looses connection.
last call?

---

### Post by Hadaka on 2013-03-05
Hi, if you want help getting your wireless working
then you must supply some information other than
its a usb wifi,"widemac'. and there are some wireless
units that will work in windows and NOT in linux.
please open a terminal by pressing ctrl/alt/t
plug in your "widemac"
then copy and paste this command.

```
 lsusb | grep -v root
```

then copy and paste the output to this
thread.
thanks.

---

### Post by eyeneedhelp on 2013-03-05
i ll do that soon as i get off this win7 comp.the download from the disc that comes with the unit has linux on it and the seller says he uses it with ubuntu,"The adapter guy" from Sheboygan wisc.
i dont know this forum well but ill try to get info here.

done;;;
report is,  cannot access susb no such file or dir

i no longer get any activity led on the usb unit and no connection on ubunto.
i was using it here minutes ago.

when i first turned on linux i had no wireless choice,just networking.

where can i find info on "susb' since i know not what im doing

---

### Post by Hadaka on 2013-03-05
Hi, this is why i stated "copy and paste this comand"
is LSUSB lower case letters..(list usb)

```
lsusb | grep -v root
```

thanks.

---

### Post by eyeneedhelp on 2013-03-05
sorry but if i could copy and paste on my linux comp i would be connected!

the system reports:,,,,,when i type in that command.

"cannot access susb    no such file or dir."

i dont know any way of saying it , thats exactly what happens when i type what you suggested.

edit 1 minute later, on the ubuntu comp i connected for about 30 seconds to a youtube link i had a day ago.
i quickly cliked another link and went there so it worked for 30 seconds!! i am on win 7 to send this.

also what do you get when you type lsub on your comp?


10 min later on win comp,the ubunto inn next room is "building confidence"1q, it stays  connected for a few minutes but while connected i paste the command and always get the same result,"cannot access susb, no file or dir"

is this normal?

---

### Post by Hadaka on 2013-03-05
hi, you get no such commnd because its
L S U S B   lsusb.

*If I plug in a usb device i get a print out of it when i enter
lsusb | grep -v root     like this............

Hadaka@the_beach:~$ lsusb | grep -v root
Bus 001 Device 002: ID 0781:5575 SanDisk Corp.
Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter

most likely because i type in the correct command.

good luck.

---

### Post by eyeneedhelp on 2013-03-05
typing exactly as you say, lower case right?
please understand, i cannot copy paste from my win7 comp here to my linux in the next room.
ok,i must have a xtra space,not used to dos like typing and fussy syntax!.
i get,
"bus 001 device 005 id 148f:5370 ralink tech rt5370wireless adapter"

i typed l susb, not lsusb

later, i dont see any install for rt5370 in the data i downloaded.
do i need drivers?

---

### Post by Hadaka on 2013-03-05
Hi, well the good new is, we now know what driver you need to 
make it work with Ubuntu, the bad news is the driver is rt5370sta
and 5370sta isn't in the kernel, it needs to be compiled after
downloading from the rawlink site. You only have the windows
computer working from what i understand. Does the wired connection
work on the computer with ubuntu??

---

### Post by eyeneedhelp on 2013-03-05
my only connection is wireless on both comps.
the ubuntu was connected for apx 10 min and i went to about 6 sites,?how come? with no driver

---

### Post by Hadaka on 2013-03-05
Hi,, I have no idea why you were able to connect and view
a few sites before it stopped working. I would hope that you
properly shut down or did the "saftely remove" option before
you removed the wireless adpter. just yanking them out of the
usb port without proper shut down or removal can damage the
wireless unit beyond repair. let's hope that is not the case. I
recall you saying it worked in the windows machine...does it 
still work with windows? also I have been digging around and
found a post where the rt5730 will work with the rt2800usb driver.
please go to your ubuntu machine and enter this command.
**Please check for typos**
```
modinfo rt2800usb | grep 5370
```

it should show one line with several numbers...one of them
being 5370
report back your findings please
thanks.

---

### Post by eyeneedhelp on 2013-03-05
yes a long string with the alias: usbv148fp5370 ,then a bunch of d,c *etc.

there is some stuff in the big download, suppose to be drivers but i dont know what to do with .
i might be able to get you the down url i used if you want a copy to see?


here.

[http://www.adapterguy.com/files/WiFiAdapter.zip](http://www.adapterguy.com/files/WiFiAdapter.zip)

this is the copy of the disc my dvd ate

---

### Post by Hadaka on 2013-03-06
Hi, that url with the zip file wouldnt do any good
because you have no way to get it on the ubuntu machine.
I am leary of having you load the rt2800 driver because you 
have some kind of driver currently loading or it wouldnt have
connected for a short time. lets try this...
at the ubuntu machine enter..

```
lsmod | grep usb
```
 lower case LSMOD
look for a number...hopefully RTxxx usb
and for mac80211 in the first colum and an RTxxx usb or whatever in the 3rd colum
any number that has usb in it.
please read this carefully....also...does the wireless usb device, the actual
plug in unit say b/g/n?

and more importantly...is the wireless router close to the computer?
please answer all 3 questions in your next post
thanks.

---

### Post by pinballwizard on 2013-03-06
Any network gurus want to lend a hand here: [http://ubuntuforums.org/showthread.php?t=2122705](http://ubuntuforums.org/showthread.php?t=2122705)

(PS, Hadaka, love the sig, I'm craving anchovy pizza for breakfast now...)

---

### Post by eyeneedhelp on 2013-03-06
@ Hadaka
If there is a driver in it?can i delete or just download a fresh copy known to be clean?
if this usb unit wont work i have another coming ? today. IF there is a ? driver in it already i dont expect the new/different one to work either.
if thats the case im not in the mood to get into a saga  to get connected to the net,as i am,easily at this moment.
id love to be a linux user but it doesnt look like it is at the level of performance as ,drat, windows is!
yes my widemac works fine here,not damaged by pulling it out of the usb port,yes i tried it on an extension cable hanging on the ceiling. when it works it doesnt care where it is.

the sw i showed you is a copy of the disk the manufacturer packed with it,best i can do.

so im waiting for ups for my final usb device.
i do very much appreciate all your efforts and help and i thank you very much.

---

### Post by eyeneedhelp on 2013-03-06
So i got a new asus usb wifi device today.
No install program like i have learned to love over the years!, just a bunch of files and cryptic gobly gook stuff i dont understand. i struggled thru this kind of stuff in the days of dos 5!! but im not up to it after all the years of those endless but easy install programs in win 3.1---98--xp--7, and all the ones in between.
ill hang around from time ton time to see if anyone finds the wifi cure for linux!!

btw the new asus does nothing,unlike the widemac that connected all by itself,(on occasion!)

---

### Post by Hadaka on 2013-03-06
Hi, just so you know, its not a linux problem, its 
a wifi manufactures problem, if they don't support
and supply dirvers for linux then it becomes difficult
at times. You wimac wireless has worked and it is loading
the driver, this is why i needed you to supply some information
to figure out what driver.
```
lsmod | grep usb
```
the wifi only needs to be plugged in, it doesnt matter if it is
working or not...it still loads the driver. here is mine...it's plugged in
and not active.
```
Hadaka@the_beach:~$ lsmod | grep usb
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              20092  1 rt73usb
rt2x00lib              48146  2 rt73usb,rt2x00usb
mac80211              393421  3 rt2x00usb,rt2x00lib,b43
 
```
as you can see it uses the rt73 driver  ....rt73usb...
this is the information i need from you to get your
wireless working

---

### Post by eyeneedhelp on 2013-03-06
the last thing i reported was
"usbv 148fp5370 and some other junk in my previous post.

are you saying that the giant file that vcame on the disc with the widemac device was usless for that product
??
it had win drivers and linux files. no good??

understand it is difficult to go next room,with hand written notes,enter it,get a response,hand write it and bring it here to type!,quite messy when i dont know what im doing

---

### Post by Hadaka on 2013-03-06
What im saying abou tthe zip file is..you ave no way to load it.
the usbv 148fp5370 is the wifi chip..the circuit inside the wifi unit.
that is not the driver. if you plug it in and then type...

```
lsmod | grep usb
```
it will most likely say what the driver is
rtxxxxusb....all i need is the one number
not tons of data
or if you want to try this command..it may load
plug in the wifi  and enter...
```
sudo modprobe rt2800usb
```

does it work?

---

### Post by eyeneedhelp on 2013-03-06
ok got something like you had.

rt280053298 1 rt 2800 usb

rt 2x00lib 8192c_common,rtlwifi

mac 80211


this is not all but what looked basic like yours


so it reported that rt2800 could not be found, but i connected anyway,very fast,for a while, sites,then as many here report,i lost conn,reconnected,slow,l???
i do get some same numbers with 2 different usb devices

im leaving in 30 min for 2 hrs

oops, missed your last post when i typed the above.
ill try it now


did you unzip the download?, i did . it has drivers for win . mac, linux,,,??what is it for?

gotta run, be bak in 2 hr.

---

### Post by Hadaka on 2013-03-06
Hi,try these commands

```
sudo modprobe -r rt2800usb
 sudo modprobe rt2800usb nohwcrypt=1
```
 *ONLY If it connects then do..
```
sudo su 
echo rt2800usb >> /etc/modules
exit
```
then do...
```
sudo apt-get update
sudo apt-get upgrade
```
post back your findings
thanks.

---

### Post by eyeneedhelp on 2013-03-07
!!! FIRST, let me quickly check in,,,on my ubuntu comp!!!

it connected with my last post and i went into town , just got back and got the surprise!

so hello world and thanks. maybe we ,you can figure out why its working!!

---

### Post by eyeneedhelp on 2013-03-07
!!! FIRST, let me quickly check in,,,on my ubuntu comp!!!

it connected with my last post and i went into town , just got back and got the surprise!

so hello world and thanks. maybe we ,you can figure out why its working!!


it asks for password??
i put in the one i started with last month before i got wifi and it doesnt tell me if good or not and i dont know what to expect.

also where do i get a list of the "mystery"codes you are giving me?!! so i can study and know a little bit about this stuff

another edit as long as i am connected its a little easier to reporte back on the same computer as i mess with!!

HOOORAAY!!!  wait till i tell my friend ART who got me into this in the first place!!

---

### Post by eyeneedhelp on 2013-03-07
well im back on my win7 comp. it was sure fun on ubuntu,,,while it lasted!!
its fast when it works,but erratic,dont know what to expect.so im done for now.

---

### Post by Hadaka on 2013-03-07
Hi, when you do a sudo command it asks for your password
when you type it in, it does not echo back what you type.
if the password was not correct, it would have said so.
did you do the commands i sent last post when you connected?
as in...```
sudo modprobe rt2800usb nohwcrypt=1
  sudo apt-get update
sudo apt-get upgrade
```
and
```
sudo su
echo rt28000usb >> /etc/modules
exit
```
sounds like its working to me,please make sure
you do these commands.
thanks

---

### Post by eyeneedhelp on 2013-03-07
ok , i got cut off before i could finish them. ill try now. 

thanks again.
ill be back later

all worked but got disconnected part way thru upgrade.system suggested try--fix-missing but that was not recognized.
i keep getting prompted to giv password for network,it interupts me when trying to type in sudo stuff.
im on win7 now since ubuntu is off line again,cant keep on.
when it decides to work its good but not steady.
when off i just leave,go back and it might connect.
btw when it did update,a lot of stuff came in. i had hope that would help,alas.
so tomorrow,,,i try more.

oh no, 2 am, still up...
ubu is working again
looking thru help file, cant make much sense of this new stuff,,yet

now gone


btw,kind of neat that i can come here on win and finish/edit a post from ubuntu comp! but i want out of win


edit, 9:50 am, connected, no internet.
also,how do i delete un neened nets in the area that show up and clutter up the mess i already have?

---

### Post by Hadaka on 2013-03-07
Hi, please do these commands to hopefully keep you
connected.
**Important..read carefully before you save the edit

open a terminal  ctrl/alt/t and enter...
```
sudo gedit /etc/modprobe.d/rt2800usb.conf
 
```
at this point the gedit editor will come up.
** there can be NO typos with this,please check 
that it is correct BEFORE you click save.
Enter this One line..
```
options rt2800usb nohwcrypt=1 
```
save and close gedit.
then boot the machine.
*IF it does not connect enter this command..
```
sudo su
echo rt2800usb >> /etc/modules
exit
modprobe rt2800usb
```
and also check it is correctly entered before
hitting enter.
thanks.

---

### Post by eyeneedhelp on 2013-03-07
Ok thanks,i just got home and i will need to hand write this as i have no connection but here on win7.

i am curious about the disc data i have with the usb unit.what is the realtek 8187l linux that shows up with the linux stuff?

i really wonder just what someone starting out fresh with a new install of ubuntu and the usb stuff i bought would go about using it?
surely it could be used by someone not deep into the coding of linux,? or ?

i asked the man i bought it from,who said he uses it,and have no answer so far.

do i assume correctly that you and others on the forum are way beyond the level of casual computer users who do email and a little surfing?

at this point i am a lot deeper than i really want to be in linux. as i mentioned, i paid my dues and enjoyed the depth of working inside the cbm and ibm hdwe and sw and interfacing,,,but no more!!

so if this doesnt produce workable results,im going to thank you all once more and bail out and scrap it all and chock it up to another life lesson!

---

### Post by Hadaka on 2013-03-07
Hi, the 8187 l is the chipset in the wifi unit, you dont have that
you have the 5370. So this means widemac uses differnt chips
for the same unit,which is not uncommon. The biggest reason
this has been difficult is because you have zero internet connection
with your linux machine. Once this is up and running,it can do
pretty much anything a windows machine can,and more. Right now
its frustrating to you because you are just learning. I would guess
you did the same when you were learning windows. Hang in there
you are almost there.

---

### Post by eyeneedhelp on 2013-03-07
geting errors,,etc is ?

i typed exactly, stuck in next room trying a third time

---

### Post by Hadaka on 2013-03-07
Hi, it's   /etc       backslash etc

why dont you carry the windows laptop into the room
with the ubuntu machine???

---

### Post by eyeneedhelp on 2013-03-07
editor reports "etc" is a dir and cancel is my option
i think its a forward slash,but regardless i get an error and cant continue

---

### Post by Hadaka on 2013-03-07
hi, that command i gave you is correct
you really need to enter it correctly for it 
to work. here is the command again..
mind the spelling and spacing..
```

sudo gedit /etc/modprobe.d/rt2800usb.conf 
```

---

### Post by Hadaka on 2013-03-07
type in this command....correctly
and tell me if your wifi comes to life.

```
sudo modprobe rt2800usb 
```

---

### Post by eyeneedhelp on 2013-03-07
sorry, i didnt see the update here on the forum , i have trouble getting updated.
i type that EXACTLY the same, or i am incapable of telling the difference so i can keep trying to no use!!

---

### Post by eyeneedhelp on 2013-03-07
it appears that i am and have been at times connected to the network,BUT  i cannot get the internet,,,with the same links i do here on win and did yesterday on ubuntu.

so im done...
its actually worse today,no conn at all

---

### Post by Hadaka on 2013-03-07
Hi, ok here is a suggestion. your windows laptop
should be portable. so log into to forums. this
thread....post #34...   code instructions i gave you.
the ubuntu machine does NOT have to have the
wifi unit plugged in to accept these commands.
so leave that page up on the laptop (windows)
and then view the commands one at a time and
enter them into the ubuntu machine. Then unplug
the wifi unit from the windows machine. plug it into
the ubuntu machine. boot and it should work.
Post #34 has the correct commands to finally get
it working for you. Untill you can get those typed in
correctly there is nothing more i can do to assist you.
thanks.

---

### Post by eyeneedhelp on 2013-03-07
tomorrow ill take a picture off the screen!!
if i can upload here ill do that.'
i dont think i misspelled "etc", thats where it stops, says its a directory and i dont know what to do when the editor says cancel

goodnite all.

---

### Post by eyeneedhelp on 2013-03-08
so i started from scratch,posted in the installation area and got no help.
am i asking too much? even with a fresh download of 12.1,erasing my previous 12.04 i still have no real results.
now i get a slow 2 second delay to mouse clicks and the same response as before on wifi with a new,fresh wifi usb adapter.
still no way to install the drivers on the disc?
how does anybody get started with this thing??

i connect to the local net but no internet connection.


total fresh new install and new fresh usb.

any help??

---

### Post by Hadaka on 2013-03-08
Hi, so you loaded 12.10 and got a different wifi
usb? What do you mean by "connect to the local net"
and not the internet?

---

### Post by eyeneedhelp on 2013-03-08
sorry, the wifi net im on now,down the hall.
also im now having trouble with that 12,1. it had a 2 sec delay from click to action. i reinstalled it from the same disc and it now never restarts so i need to clear that up??


edit,,,i just started reinstalling 12.04, i gave up on 12.1, had it running once,but slow,so when i nreinstalled it,it never worked right again.???i have no clue.

---

### Post by Hadaka on 2013-03-08
Hi, so "down the hall" is a different wireles name
but it is still connected to the internet. anyway, yes
if you cant boot to 12.10 it will be difficult to do any
trouble shooting. If you dont mind me suggesting...
12.04 LTS is probably a better choice because it has
support untill 2017 where as 12.10 only has support
for maybe another year. It is newer but for everyday
use I think 12.04 is a better choice because of the long
term support. Just my prefrence,whic ever you decide
we will see if we can get your wireless working.

One last question i have is....the windows machine..
is it a laptop and is the ubuntu machine a desktop?
thanks.

---

### Post by eyeneedhelp on 2013-03-08
yes win is laptop,ubuntu is desktop and i am reinstalling 12.04 at this moment

---

### Post by Hadaka on 2013-03-08
hi, great, once you get 12.04 loaded dont worry just yet
about getting connected to the internet and getting the wifi
working. Leave the windows laptop connected to the internet
and place the laptop near the ubuntu desktop so you can simply
look over at the screen of the laptop and enter commands into
the ubuntu desktop.   sound ok ?

---

### Post by eyeneedhelp on 2013-03-08
yeah,ill try to move it. i did a quik check,got to google but no further,no sites.
thats with the orig usb,widemac,not the new one.

---

### Post by Hadaka on 2013-03-08
great, once you have the laptop in position next to
the ubuntu desktop, let me know and we will try to
get you properly connected. In the meantime please
dont try to connect to anything with the ububtu untill we can figure out
what is going on
thanks.

---

### Post by eyeneedhelp on 2013-03-08
ok i cam try it
how to keep connected here?  quik reply?

i dont know the forum operation

---

### Post by Hadaka on 2013-03-08
ok, tell me where the widemac usb wirless is ?
in the windows laptop or the ubuntu desktop?

---

### Post by eyeneedhelp on 2013-03-08
in ubuntu

---

### Post by Hadaka on 2013-03-08
Ok, well see if we can wake it up.please only type in
what i send you. If it connects..dont try to go to a web site.
just report back and i will give you the next command.
here is the first command.

in terminal....ctrl/alt/t

```
sudo modprobe rt2800usb nohwcrypt=1
```

take your time, no rush....ok?

---

### Post by eyeneedhelp on 2013-03-08
ok got password,back to prompt

---

### Post by Hadaka on 2013-03-08
did you type in your password and the command?

---

### Post by eyeneedhelp on 2013-03-08
yes i got past that and back to password

---

### Post by Hadaka on 2013-03-08
ok so you typed in the command with no errors and
are back at the prompt.  Next lets see if it will now
connect to the internet. Try to connect, you should
get a google page if you do,, dont go to any sites
just report back for the next command.
thanks

---

### Post by eyeneedhelp on 2013-03-08
sorry,got a friend phone call.
got one  no connect,then 2nd try got google

---

### Post by Hadaka on 2013-03-08
great !..ok..leave the google page up and lets
update it with all the goodies

in terminal ctrl/alt/t   and the google page still up
please do..

```
sudo apt-get update
```

several things will print out, when its done let me know
but again..dont try to go to any other sites ...and leave the 
google page up
thanks

---

### Post by varunendra on 2013-03-08
Wow! We are having quite a battle here :P

@ eyeneedhelp, (interesting user name by the way ;))
Sorry if I missed a post already stating it, but do you have an option to transfer tiny files between the windows and linux computers (a pen drive, memory card etc.)?

If yes, why don't you just copy-paste suggested commands from windows to a text file > carry it to ubuntu > copy-paste from it to the terminal ?
You may do the same to carry the terminal outputs to the windows lappy and post them here.

Oh, by the way, regarding posting of the file Vs. its cintents from windows, you might wish to read this post : [http://ubuntuforums.org/showthread.php?t=2122144&p=12548633#post12548633](http://ubuntuforums.org/showthread.php?t=2122144&p=12548633#post12548633)

---

### Post by eyeneedhelp on 2013-03-08
all failedaybe not all?? some ok??

---

### Post by eyeneedhelp on 2013-03-08
i need to reset forum each time to find you  
if there were downloads it was very fast, then "failed to fetch",,,

---

### Post by Hadaka on 2013-03-08
Thats ok..is the google page still up?

---

### Post by eyeneedhelp on 2013-03-08
yes

im thinking qwhen we did that command yesterday there was a lot of stuff updated huh

---

### Post by Hadaka on 2013-03-08
yes but you reloaded 12.04 so its all new now.
ok lets make sure the driver gets loaded every time
you start the computer..
in terminal ctrl/alt/t  please enter..

```
sudo su
echo rt2800usb >> /etc/modules
exit
```

make sure you have 2 of these >> in the command.

report back any errors

thanks.

---

### Post by eyeneedhelp on 2013-03-08
ok not much happened no error

---

### Post by eyeneedhelp on 2013-03-08
im on ubuntu now!!!

when i said it downed more before,that was 12.04

i just tried 12.1 this aft

---

### Post by Hadaka on 2013-03-08
awesome ! you are doing great.
ok this next command brings up the gedit editor
once it is up...let me know and i will give you what
to type in.
in terminal ctrl/alt/t please enter.
```
sudo gedit /etc/modprobe.d/rt2800usb.conf 
```

leave this editor page up for the next command.

report back please

---

### Post by eyeneedhelp on 2013-03-08
ok got it
new box to type in huh

---

### Post by Hadaka on 2013-03-08
yup...new box to type in
here is the one line to type in..

```
options rt2800usb nohwcrypt=1 
```

proof read so its 100% correct then
click the save symbol and the close by clicking the
red dot..upper left corner.
report back please

---

### Post by eyeneedhelp on 2013-03-08
ok saved,,? closed, back to root prompt


on win,,lost,then found int on ubuntu

---

### Post by Hadaka on 2013-03-08
great !..ok now its time to restart
click the star shaped symbol next to the time.....upper right corner
then..in the dropdown box...click shutdown
then..the next box click...Restart    left lower corner
report back if it restarts ok.
thanks

---

### Post by eyeneedhelp on 2013-03-08
when i clik and release i loose what was open so it shut off and i restart

i notice that when i clik the wireless symbol i need to hold the mouse button???

---

### Post by eyeneedhelp on 2013-03-08
restarted but back where we wehe yesterday!! no connection to internet

connect to network wifi but no forum,no internet

---

### Post by eyeneedhelp on 2013-03-08
having trbl here on win also?

---

### Post by Hadaka on 2013-03-08
ok..maybe the router is feeling flakey.
do you see any available wifi connections
when you click the symbol next to the envelope
upper right corner?

---

### Post by eyeneedhelp on 2013-03-08
yes i see the 3 i always see anjd im connected to my wifi because its name is up with the "disconnect "prompt.
sometime it says disconnected.
i clik the name and thpe pass and get conn but no web page.
same as last week!

---

### Post by eyeneedhelp on 2013-03-08
ive been here relentlessly for 13 hours now,,thanks so much but now im crashing!!
ill report back tomorrow

---

### Post by Hadaka on 2013-03-08
ok..thats progress
enter this command and tell me
what you see..ignore any lines with a # in front of them
just type back the 2 or things with no #

```
cat /etc/modules
```
thanks

---

### Post by eyeneedhelp on 2013-03-09
rt2800usb


im on my windows computer.

at 11pm i will celebrate one week on this forum. i got here with my ubuntu comp and the then new widemac us wifi with no driver installed. last sat night i watched utube videos,went to my car forum and finally found this forum to learn about ubuntu.

ive tried 12.04 and 12.1, two different usb devices,asked this question over and over in ?three threads: 
"how does a newcomer install a new usb wifi device in a fresh new ubuntu computer?:

there are no answers!!
 the sw disc that comes with the device will instal it on my windows xp comp but not on linux even though it has a linux file!!

is it proper for me to keep asking this question,or should i just leave,well enough alone?!!

or,"has anybody here ever done that??

next room,my ubuntu sits,no connection to int after one week of relentless attempts.

are you guys really using linux here??!!!

last nite i installed my 2nd usb,asus on another windows xp computer and got on the net in abt 5 minutes!

---

### Post by Hadaka on 2013-03-09
Good morning, I am sorry this has been so difficult for you.
last post you mentioned you can see 3 different connections
with the ubuntu machine. This means the wifi is working.
have you configured your conection settings? as in set to wep 
or whatever and the passphrase?

---

### Post by Hadaka on 2013-03-09
try this
in terminal ctrl/alt/t
code:

ping 8.8.8.8

tell me what happens
thanks.

---

### Post by eyeneedhelp on 2013-03-09
i typed a long and detailed answer ON UBUNTU and cliked send as i always did,the system lost it and im not good at retyping.  so im back to windows 7. 
lets face it its eratic and im not going to suffer with it when i can just clik on win7 and be done with it.

btw i will ocassionally continue to look for an answer to my "no response"question; "how does a person install a usb wifi device on a fresh new linux computer?",,,!!

if i ever get an answer ill try again!

---

### Post by Hadaka on 2013-03-09
Hi, I opened that zip file you sent from the drivers-guy site.
here is the first part of the READ ME file.
Release Date: 2006-02-09, ver 1.2 
RTL8187 Linux driver version 1.2 
 
   --This driver supports RealTek RTL8187 Wireless LAN driver for  
     Fedora Core 2/3/4/5, Debian 3.1, Mandrake 10.2/Mandriva 2006,  
     SUSE 9.3/10.1/10.2, Gentoo 3.1, etc. 
   - Support Client mode for either infrastructure or adhoc mode 
   - Support WEP and WPAPSK connection

1. you dont have the rtl8187 chip set in that wireless unit
2. ubuntu 12.04 has a current kernel release -  the zip file doesnt
3. this driver is 7 years old....way outdated
4. its not going to make your widemac wireless work.

If i say to you  "Midori" most likely it means nothing to you
it's the japanese word for "Green"
MY point here is Linux is NOT windows
learning linux is somewhat like learning a new language. Linux
can do every thing windows can and thousands of things windows
will never be able to do.

I know you are frustrated, and to answer your question there are several
ways people use a usb wifi adaptor with linux
1.plug it in and it just works
2.load the tar file that hopefully comes with it and is correct
3. modify or use a driver that is already part of the kernel that works with the wifi chip set.
4.download the driver from the usb wifi web site
5. build your own driver
6. countless other methods.
If you had a hardwire connection, then you could copy and paste the results of all the commands
you have been given. Its very difficult to determine just what the problem is without seeing those
results. You being new to linux, dont know what you dont know, and we have no idea just exactly
what you do know.I would strongly suggest to get a ethernet cable,plug directly into the router
and then come here for help. If that is impossible, it is still possible to get your unbuntu machine
up and running, we know this for a fact..because it has more than once, connected to the internet
with the widemac usb wifi.
There are several people on here, including myself that will give you any kind of support and
help that we can, it's up to you.
thanks.

---

### Post by eyeneedhelp on 2013-03-09
well, 3 steps forward,2 steps back!. i was cruising along,rereading this thread from # 1 to see what i missed and to see if i can understand a little after cooling down from the frustration. i moved the computer and am now more connectedso the position affected it.
i reran the update because i didnt feel like it ran long  the last time and this time it did. i dont know what it did but  it still works.
i cannot run youtube videos like i did the first night??. tried downloading flash player and for a while everything seemed to freeze and the mouse didnt do much or anything so i pulled the plug and walked away in lieu of throwing it off the deck and using it for 12 ga. practice.

it came back alive,lucky it!, so im skipping you tube for now.
i wasnt fully grasping your info on the driver and partly because i expect a package to work even if not the latest. so i di reread the entire thread and got here.btw im usind a monitor for the new xp comp i got and i rotated it 90 degrees so it reads like a page should
and i like it, i think ill do that to my 37 in tv since i use it most for my laptop 2nd display!
so my games/most stuff in the 12.04 ubuntu do nothing. am i missing something else thats simple?

im going to relax on another forum before attempting email.

later.
oh yes,this IS the ubuntu machine!, and if this longest type does not make it i may toss it in the yard,,,

---

### Post by Hadaka on 2013-03-09
Glad to hear you calmed down and got it working ..
congratulations !  this command will help to view vids
and you-tube.
```
**sudo apt-get install ubuntu-restricted-extras**

 
```
thought i'de make it easy to read...

---

### Post by eyeneedhelp on 2013-03-09
ill try that.

i am looking at the asus , since i have it if i can figure its driver i can give it to my friend who got me into this mess! so he can suffer too.
i found the number obo5:17ab using thr commands we used for my usb, does that mean anything?

the 17ab is like the ?number you found for widemac

---

### Post by eyeneedhelp on 2013-03-09
btw i also found the # for my usb for my mouse! im snooping around
i need a printout of commands i can use to snoop and what to br careful with if im giong to have any fun here!

---

### Post by eyeneedhelp on 2013-03-09
btw i also found the # for my usb for my mouse! im snooping around

---

### Post by eyeneedhelp on 2013-03-09
got to the end of that giant download and the eula cant be accepted. it says ok but a clik does nothing

---

### Post by eyeneedhelp on 2013-03-09
got to the end of that giant download and the eula cant be accepted. it says ok but a clik does nothing

---

### Post by eyeneedhelp on 2013-03-09
youtube,every time says need to load a new flash,i did it 4 times ??

also i cant open anything but the calculator,no games nothing opens,well the spreadshht i dont need

---

### Post by Hadaka on 2013-03-09
Hi, im not familure with asus numbering, there are probably some other 
numbers in that printout as well. I would suggest before you start loading
games and whatver else, to make sure your 12.04 is running stable.
you said you did the sudo apt-get up date. did you also do...
```
sudo apt-get upgrade 
``` that doesnt upgrade to 12.10
it just up grades the operating goodies.

I'll be back in an hour or so and see how that went.
thanks.

---

### Post by eyeneedhelp on 2013-03-09
ill be sleeping, no games,no video which i had last sat at this very hour after just plugging in the usb without sw!.the last thing it did as often does is freeze where the mouse pointer moves but cliking does nothing,no open,no close,no drag. so i pull the plug out of the wall and give up ,,yet again..it really is frustrating,the worst comp experience ive had in years. i should quit and i may,,,,i will sleep on it,,,

oh the upgrade had errors

---

### Post by eyeneedhelp on 2013-03-11
FINALLY,reran the ugrade and it took, video now works.
i moved to a new location and get consistant connections.
still dont find much intuitive operations,its all like a root canal!,still cant play freecell or any game and i suppose its simple but not for me.


oh i added a hard drive and found some ?leftover linux stuff on it,some stuff that ubuntu wont read, probably windows? but cant put anything there . must need to be enabled??

so i decided to continue the struggle, actually got a new email address working,hooraah...

i stumbled into the method ,simple, to play a game.

wifi now working thru help from forum people,thanks all.
dont know how to mark it fixed. ill keep looking!!


i couldnt find solved here when i edit like i did on another so ill not worry about it

---

### Post by sir4taye on 2013-04-06
> **Hadaka said:**
> Hi,, I have no idea why you were able to connect and view
a few sites before it stopped working. I would hope that you
properly shut down or did the "saftely remove" option before
you removed the wireless adpter. just yanking them out of the
usb port without proper shut down or removal can damage the
wireless unit beyond repair. let's hope that is not the case. I
recall you saying it worked in the windows machine...does it 
still work with windows? also I have been digging around and
found a post where the rt5730 will work with the rt2800usb driver.
please go to your ubuntu machine and enter this command.
**Please check for typos**
```
modinfo rt2800usb | grep 5370
```

it should show one line with several numbers...one of them
being 5370
report back your findings please
thanks.

I have "Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter" and fresh installs of any version after 11.04 use the "rt2800usb" by default. This gives intermittant connectivity. It always looks connected, but fails to give data throughput when it feels like it and it seems less frequently with time. 

modinfo reports this----
     modinfo rt2800usb | grep 2870
firmware:       rt2870.bin
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*

This usb "dongle" worked great "out of the box" for "PNP" for at least 3 years of new latest release intsalls. 

Can you give a step by step on compiling to get the old drivers working in place of these new defaults?

---

