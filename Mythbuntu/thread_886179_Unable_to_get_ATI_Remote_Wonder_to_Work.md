---
title: "Unable to get ATI Remote Wonder to Work"
date: 2008-08-10
forum: Mythbuntu
---

### Post by murbanci on 2008-08-10
I am unable to get my ATI remote wonder to work with Mythbuntu 8.04.  It was working fine on the previous version.  I have completly reinstalled and have tried enabling the remote in MCC.  I also tried following the instructions on the mythtv wiki for the remote but that doesnt seam to be working any more.  Also, when I try to run irw I get: "connect: Connection refused"

Any help would be greatly appreciated!

---

### Post by lutz7755 on 2008-08-10
I'm having the same problem.  I'm using the XBOX remote, but it uses the ati_usb module.

irw fails, and kill lircd.  /dev/lirc0 does not exist.  I'm having great difficulty finding any info on how this is all supposed to work out.

this all worked fine in 7.10.

---

### Post by lutz7755 on 2008-08-10
Here's the output of "dmesg"

[ 4631.733222] lirc_dev: IR Remote Control driver registered, major 61 
[ 4631.743960] 
[ 4631.743962] lirc_atiusb: USB remote driver for LIRC $Revision: 1.66 $
[ 4631.743965] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[ 4631.753128] lirc_atiusb[4]: inbound endpoint not found
[ 4631.753148] usbcore: registered new interface driver lirc_atiusb


seems the "inbound endpiont not found" is a bit of an issue.  /dev/lirc0 is never created, so nothing else works.  Anyone have any ideas on how to troubleshoot this issue?

thanks,
matt

---

### Post by lutz7755 on 2008-08-11
I found this out there

[http://xbmc.org/forum/showthread.php?t=33418&page=2](http://xbmc.org/forum/showthread.php?t=33418&page=2)

which helped.  Now the module loads, and /dev/lirc0 exists.  However, it still crashes when I run "irw" and does not work within myth.

any ideas?

---

### Post by murbanci on 2008-08-11
Right now im not even getting the remote to show up using dmesg or lsmod.  It was earlier, i dont know what i did :( any more suggestions?

---

### Post by nickrout on 2008-08-11
> **lutz7755 said:**
> I found this out there

[http://xbmc.org/forum/showthread.php?t=33418&page=2](http://xbmc.org/forum/showthread.php?t=33418&page=2)

which helped.  Now the module loads, and /dev/lirc0 exists.  However, it still crashes when I run "irw" and does not work within myth.

any ideas?

What crashes? irw? the whole machine? what error messages or symptoms of the crash do you experience?

---

### Post by lutz7755 on 2008-08-11
hmm... well, it looks like in the course of my troubleshooting I had changed hardware.conf to reflect /dev/lirc/0 instead of /dev/lirc0.  After I fixed it and rebooted, lirc seems to be working.  "irw" doesn't crash lirc anymore.  It still doesn't display anything, but "mode2" does, so I think I just need to modify my lircd.conf file and get it right.

so, to summarize my problem, it looks like it was the xpad issue that was getting loaded before lirc.  

sorry for hijacking your thread murbanci, I thought we had the same issue. You may be having something similar though... I thought the ATI remote was getting kernel support, so maybe it's being loaded and then lirc can't access it or something?

---

### Post by murbanci on 2008-08-11
Yea, I thought we might have had the same problem too.  I remember I had this same problem on the previous version of mythbuntu but that fix isnt working for this version :(

---

### Post by lutz7755 on 2008-08-12
I should have said that I also still get the "connection refused" when running irw, so it may be something with the ati_usb driver.  What happens when you run mode2?  (sudo mode2 /dev/lirc0)?

do you even have a /dev/lirc0?

---

### Post by murbanci on 2008-08-12
I dont have /dev/lirc0 so i guess its not even regonizing the reciever.  I finally broke down earlier and got a MCE Remote on ebay.  It would still be great to get this one to work tho.

---

### Post by nickrout on 2008-08-13
> **murbanci said:**
> I dont have /dev/lirc0 so i guess its not even regonizing the reciever.  I finally broke down earlier and got a MCE Remote on ebay.  It would still be great to get this one to work tho.

What do you have then?  /dev/lirc/0? /dev/lirc1 ?

Hint, type

```
ls /dev/lirc<tab><tab>
``` and the shell will show you what options exist.

---

### Post by murbanci on 2008-08-13
There isnt even a /dev/lirc there is /dev/lircd, however.

---

### Post by lutz7755 on 2008-08-14
that's what was happening to me too, so it looks like lirc can't find the remote, for whatever reason.

what do you see in if you do a "cat /var/log/daemon.log | grep lirc" ??

---

### Post by wmwong on 2008-08-14
hi guys, i've been reading through post after post, thread after thread, trying to get my ati remote wonder working with mythbuntu 8.0.4 as well. i think i've had some success, and would like to share.

i followed the wiki guide at mythtv for opensuse 10.2: [http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder]("http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder")

however, i made some changes (starting from a clean install and after doing the usual ubuntu updates).

step 1: instead of blacklisting ati_remote, i blacklisted lirc_atiusb (blacklist lirc_atiusb in /etc/modprobe.d/blacklist)
step 2: not needed
step 3: not needed
step 4: plug it in! (ps -ef | grep lircd should show that lircd is now running)
step 5: my output looked quite similar
step 6: not needed
step 7: i copied the lircd.conf, but instead of /etc/lircd.conf, i modified /etc/lirc/lircd.conf
step 8: again, i copied the lircrc, but instead of /home/mythtv/.mythtv/lircrc, i modified /home/wmwong/.lirc/mythtv (chown is not required)
step 9: restart using /etc/init.d/lirc restart
step 10: should show that lircd is running
step 11: i know get irw connected and detecting button presses (hit ctrl-c to stop)
step 12: not needed

after this, make sure you reboot your system. for me, going right into the frontend DID NOT work. i had to reboot in order for the remote to come alive. i probably could have just restarted the frontend, but i rebooted for safety, and it worked.

if i go back into the terminal after a reboot, irw now works fine.

i do notice certain dead keys, but that may just be a key mapping problem?!?! im pretty happy with at least being able to navigate the mythtv menu. i discovered that traveling back to the previous screen on the frontend, i hit 'E' (escape? again, a key mapping issue i hope!) my 'OK' button DOES NOT work at the moment, and i have not tried playing anything yet, as i haven't put anything on the system yet.

hopefully, that'll get you guys going. if you figure out the key mapping stuff, please do post. this is very frustrating, but at least it looks like there's light at the end of the tunnel!

good luck!

---

### Post by lurch89 on 2008-08-24
I was able to get it working following this post. Though, yes the mapping is off a little, it works well enough.

The only key that I have tried and haven't found is the Menu key. The letters hold the clear and pg up pg down buttons, but no menu key. Anyone a) know how to remap, or b) know which one is menu?!?!?

---

### Post by mark467 on 2008-09-04
I followed the above and finally got farther than any others before that i have tried.

it all seems to be right but i get no response from front end.
irw give msgs like 0000001448730000 00 mouse-down ati_remote

and so on. any ideas as to why front end dosent respond.

btw before i followed the above i selected ati remote kernel mode in mmc infrared devices

---

### Post by d0rax on 2008-09-18
just writing to confirm that wmwong's posting helped me a lot:

in my case I only needed the lircd.conf
(did not do any blacklist) 

my steps:
tail -F /var/log/messages
(plug in usb receiver)
/var/log/message will reflect that it detected the newly plugged device.  (ctrl-c to quit)

don't know if it's necessary to install lirc but I did:
sudo apt-get install lirc
- on the config screen pick ati/nvidia x10 kernel... (don't know if this matters)

I also restarted lircd a couple of times. 

to confirm that the receiver is receiving message from the remote:
sudo mode2 --device=/dev/lirc0

everytime you press a button on the remote, something will show up  (ctrl-c to quit)

this is the point where i got stuck. "irw" does not return anything when I press a button. 

after copying the lircd.conf in the article into my /etc/lircd.conf, and restarting lircd,  "irw" now returns something when i press a button. 

I also copied the lircrc in the article into my ~/.mythtv/ 

this is on a dell 530 with ubuntu hardy preinstalled.

---

### Post by mark467 on 2008-09-22
OK got mine working with the above post. I just need better keymappings the top row (tv dvd web menu) dont work but nav arrows at bottom and the play fwd rev work yeah!!

---

### Post by mark467 on 2008-10-18
anyone get better keymappings for this remote

---

### Post by SiHa on 2008-10-20
You can generate your own mappings easily enough.

I guess you want these configured as jumppoints? These are keys that will perform the same function no matter where you are in Myth. I use F5-F8, I think these are set to teletext or subtitle menu colours in Myth, I don't use these, so there's no conflict.

Edit your lircrc file, and edit the entries for these buttons (or create them if the don't exist).

```
begin
    prog = mythtv
    button = TV
    config = F5
    repeat = 0
    delay = 0
end
```

Then you'll need to edit the keybindings within Mythtv. Restart LIRC```
sudo /etc/init.d/lirc restart
```...and Mythfrontend.

Now go to the 'Edit Keys' menu, It's in one of the setup sub-menu's.

On the left there is a list of Mythtv states (LiveTV, Program Guide...) one of them will be '**JumpPoints**', select this and you will get a list on the right of available Jumppoints, so scroll to the one you want and select it, you will be prompted to press a key. Press the remote key that you want to bind to this function. You will probably get a warning that this conflicts with a global assignment. If you're happy to lose the one it conflicts with, hit enter, else hit esc.

If you get **'Unknown key pressed'** then you haven't got the buttons properly defined, there's probably a naming mismatch between lircd.conf and .lircrc.

HTH

Simon

---

### Post by illwill on 2009-01-05
In Mythbuntu 8.10: I can't seem to get this figured out. I made sure the files were in the right place (lircd.conf, lircrc) Mythbuntu seems to automatically symlink them to the right places (from /etc/lirc/)

I black listed lirc_atiusb. 

root@mediabox:/etc/lirc# lsmod|grep -i ati
lirc_atiusb            26160  0
lirc_dev               22216  1 lirc_atiusb
usbcore               175376  5 lirc_atiusb,usbhid,ehci_hcd,ohci_hcd


root@mediabox:/etc/lirc# mode2 --device=/dev/lirc0
code: 0x1448730000
code: 0x144b760000
code: 0x144b760000
code: 0x1448730000

root@mediabox:/etc/lirc# irw
root@mediabox:/etc/lirc# ps -ef|grep lircd
root@mediabox:/etc/lirc#


So when I type irw it seems to shut down lircd, but when I do mode2 on the /dev/lirc0 device I can see the output from pressing keys on my remote.

Jan  5 14:50:11 mediabox lircd-0.8.3[13063]: accepted new client on /dev/lircd
Jan  5 14:50:11 mediabox lircd-0.8.3[13063]: couldn't claim USB interface: Device or resource busy
Jan  5 14:50:11 mediabox lircd-0.8.3[13063]: caught signal

When I unplug the remote then plug it back in /var/log/messages says:

Jan  5 14:52:41 mediabox kernel: [ 2455.208019] usb 1-2: new low speed USB device using ohci_hcd and address 8
Jan  5 14:52:41 mediabox kernel: [ 2455.458827] usb 1-2: configuration #1 chosen from 1 choice
Jan  5 14:52:41 mediabox kernel: [ 2455.462345] lirc_dev: lirc_register_plugin: sample_rate: 0
Jan  5 14:52:41 mediabox kernel: [ 2455.475786] lirc_atiusb[8]: X10 Wireless Technology Inc USB Receiver on usb1:8


here is my messages file from a fresh reboot:
Jan  5 14:58:12 mediabox kernel: [   35.800822] lirc_dev: IR Remote Control driver registered, major 61
Jan  5 14:58:12 mediabox kernel: [   35.815804]
Jan  5 14:58:12 mediabox kernel: [   35.815805] lirc_atiusb: USB remote driver for LIRC $Revision: 1.69 $
Jan  5 14:58:12 mediabox kernel: [   35.815812] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
Jan  5 14:58:12 mediabox kernel: [   35.825383] lirc_dev: lirc_register_plugin: sample_rate: 0
Jan  5 14:58:12 mediabox kernel: [   35.832026] lirc_atiusb[2]: X10 Wireless Technology Inc USB Receiver on usb1:2
Jan  5 14:58:12 mediabox kernel: [   35.847026] usbcore: registered new interface driver lirc_atiusb

& daemon.log only says:
Jan  5 14:59:24 mediabox lircd-0.8.3[7316]: lircd(userspace) ready


Should I be doing anything with the /etc/lirc/hardware.conf file? It looks like this right now:

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="ATI/NVidia X10 RF (userspace)"
REMOTE_MODULES=""
REMOTE_DRIVER="atilibusb"
REMOTE_DEVICE="lirc0"
#REMOTE_LIRCD_CONF="atiusb/lircd.conf.atilibusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
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
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

---

### Post by computermacgyver on 2009-01-11
I think the hardware.conf file is indeed your problem, illwill . I was at the same state and then adjusted my /etc/lirc/hardware.conf to the following:
```

# /etc/lirc/hardware.conf
#

#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER="default"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""



#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

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
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="atiusb_ch1"
REMOTE_VENDOR="ATI Remote Wonder"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL=""
RECEIVER_VENDOR=""

```

I also installed "gome-lirc-properties" from the standard software repositories and set the remote to:
Use different remote control
Manufactuer: ATI Remote Wonder
Model: atiusb_ch1

You should then be able to press any buttons and see the results in the Configuration Test section of gnome-lirc-properties

My .lircrc file has entries for mythtv (currently unused), mplayer, and rhythmbox
```

#irexec and irxevent
#use this for global commands
#irexec should run as a global deamon

begin
prog = irexec
button = BOOK
config = rhythmbox
repeat = 2
end

begin
prog = irexec
button = DVD
config = totem
repeat = 2
end

begin
prog = irexec
button = WEB
config = firefox
repeat = 2
end

#keyshortcuts
begin
prog = irxevent
button = DOWN
config = Key Down CurrentWindow
repeat = 2
end

begin
prog = irxevent
button = UP
config = Key Up CurrentWindow
repeat = 2
end

begin
prog = irxevent
button = Left
config = Key Left CurrentWindow
repeat = 2
end

begin
prog = irxevent
button = RIGHT
config = Key Right CurrentWindow
repeat = 2
end

begin
prog = irxevent
button = OK
config = Key Return CurrentWindow
repeat = 2
end


### MPlayer lirc setup
#
# Remember to ln -s ./.mythtv/lircrc ../.lircrc for mplayer to work!

# Show OSD
begin
prog = mplayer
button = tv_on_demand
repeat = 3
config = osd
end

# Pause playback
begin
prog = mplayer
button = pause
repeat = 3
config = pause
end

begin
prog = mplayer
button = play
repeat = 3
config = pause
end

# Stop playback and exit
begin
prog = mplayer
button = stop
repeat = 3
config = quit
end

# Mute
begin
prog = mplayer
button = mute
repeat = 3
config = mute
end

# Seek back 10 seconds
begin
prog = mplayer
button = rewind
repeat = 3
config = seek -10
end

# Seek forward 30 seconds
begin
prog = mplayer
button = fastforward
repeat = 3
config = seek +30
end

# Quit
begin
prog = mplayer
button = e
repeat = 3
config = quit
end

#
# MythTV native LIRC config file for
# the ATI-Wonder Remote
# using lirc_atiusb driver
#

begin
prog = mythtv
button = a
config = E
repeat = 2
end

begin
prog = mythtv
button = b
config = O
repeat = 2
end

#begin
#prog = mythtv
#button = tv
#config = Key Alt-T CurrentWindow
#repeat = 2
#end

begin
prog = mythtv
button = stop
config = Esc
repeat = 2
end

begin
prog = mythtv
button = fastforward
config = Right
repeat = 2
end

begin
prog = mythtv
button = rewind
config = Left
repeat = 2
end

begin
prog = mythtv
button = max_window
config = V
repeat = 2
end

begin
prog = mythtv
button = pause
config = P
repeat = 2
end

begin
prog = mythtv
button = play
config = P
repeat = 2
end

begin
prog = mythtv
button = mute
config = F9
repeat = 2
end

begin
prog = mythtv
button = vol-down
config = F10
repeat = 2
end

begin
prog = mythtv
button = vol-up
config = F11
repeat = 2
end

begin
prog = mythtv
button = f
config = PgDown
repeat = 2
end

begin
prog = mythtv
button = d
config = PgUp
repeat = 2
end

begin
prog = mythtv
button = c
config = F4
repeat = 2
end

begin
prog = mythtv
button = e
config = Esc
repeat = 2
end

begin
prog = mythtv
button = cursor-right
config = Right
repeat = 2
end

begin
prog = mythtv
button = cursor-left
config = Left
repeat = 2
end

begin
prog = mythtv
button = cursor-up
config = Up
repeat = 2
end

begin
prog = mythtv
button = cursor-down
config = Down
repeat = 2
end

begin
prog = mythtv
button = chan-up
config = Up
repeat = 2
end

begin
prog = mythtv
button = chan-down
config = Down
repeat = 2
end

begin
prog = mythtv
button = rewind
config = Left
repeat = 2
end

begin
prog = mythtv
button = ok
config = Enter
repeat = 2
end

begin
prog = mythtv
button = 1
config = 1
repeat = 2
end

begin
prog = mythtv
button = 2
config = 2
repeat = 2
end

begin
prog = mythtv
button = 3
config = 3
repeat = 2
end

begin
prog = mythtv
button = 4
config = 4
repeat = 2
end

begin
prog = mythtv
button = 5
config = 5
repeat = 2
end

begin
prog = mythtv
button = 6
config = 6
repeat = 2
end

begin
prog = mythtv
button = 7
config = 7
repeat = 2
end

begin
prog = mythtv
button = 8
config = 8
repeat = 2
end

begin
prog = mythtv
button = 9
config = 9
repeat = 2
end

begin
prog = mythtv
button = 0
config = 0
repeat = 2
end

begin
prog = mythtv
button = record
config = R
repeat = 2
end

begin
prog = mythtv
button = check
config = Enter
repeat = 2
end

##Rhythmbox
##Codes are at: http://svn.gnome.org/viewvc/rhythmbox/trunk/plugins/lirc/rb-lirc-plugin.c?view=log
#
#

###########Commands as of 2009-Jan-10
#55 	#define RB_IR_COMMAND_PLAY "play"
#56 	#define RB_IR_COMMAND_PAUSE "pause"
#57 	#define RB_IR_COMMAND_PLAYPAUSE "playpause"
#58 	#define RB_IR_COMMAND_STOP "stop"
#59 	#define RB_IR_COMMAND_SHUFFLE "shuffle"
#60 	#define RB_IR_COMMAND_REPEAT "repeat"
#61 	#define RB_IR_COMMAND_NEXT "next"
#62 	#define RB_IR_COMMAND_PREVIOUS "previous"
#63 	#define RB_IR_COMMAND_SEEK_FORWARD "seek_forward"
#64 	#define RB_IR_COMMAND_SEEK_BACKWARD "seek_backward"
#65 	#define RB_IR_COMMAND_VOLUME_UP "volume_up"
#66 	#define RB_IR_COMMAND_VOLUME_DOWN "volume_down"
#67 	#define RB_IR_COMMAND_MUTE "mute"
#68 	#define RB_IR_COMMAND_QUIT "quit" 
####################

begin
prog = rhythmbox
button = PLAY
config = playpause
repeat = 2
end

begin
prog = rhythmbox
button = STOP
config = stop
repeat = 2
end

begin
prog = rhythmbox
button = VOL_DOWN
config = volume_down
repeat = 2
end

begin
prog = rhythmbox
button = VOL_UP
config = volume_up
repeat = 2
end

begin
prog = rhythmbox
button = MUTE
config = mute
repeat = 2
end

begin
prog = rhythmbox
button = REW
config = previous
repeat = 2
end

begin
prog = rhythmbox
button = FFWD
config = next
repeat = 2
end

begin
prog = rhythmbox
button = POWER
config = quit
repeat = 2
end

#totem

```

---

### Post by illwill on 2009-01-12
Thank you very much Mac. I went and bought an [MCE remote]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880121003") though and it worked pretty good right out of the box so I'm pretty happy.
I might try this old ATI Remote Wonder again though on my laptop or something just to see if it works. Thanks again!

---

### Post by tobiz on 2009-03-11
I've bought a cheap (~GBP 10) ATI Wonder look-a-like remote with USB connection, It says "UR86E PC Remote" on the back of the remote.  I'm running Mythbuntu 8.10.  If I install the remote as an ATI/Nvidia X10 RF from Myth CC I can get irrecord to record (most) of the keycodes from device=/dev/lirc0. However, irw doesn't show an keys pressed, mode2 complains 
mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory

or

mode2 -d /dev/lirc0
Please use the --raw option to access the device directly instead through the abstraction layer.

This has a strong feeling it should work but doesn't.  Any ideas how to track down the problem?

---

### Post by tobiz on 2009-03-24
I now have the UR86E X10 RF remote working after finding this site [http://www.vanstormbroek.nl/blog/?p=13#comment-342]("http://www.vanstormbroek.nl/blog/?p=13#comment-342"). I also have some keys now controlling MythTV eg Up, Down, Ok, Exit. Just needs work to map all the keys via /etc/lirc/lircd.conf to ~/.lircrc.conf -progress at least!

---

