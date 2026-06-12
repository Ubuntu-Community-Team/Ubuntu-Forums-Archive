---
title: "Hauppauge Wintv-pvr 150 remote does not work"
date: 2008-05-01
forum: Mythbuntu
---

### Post by ati on 2008-05-01
Hallo,

I am new to Mythbuntu, and novice with linux ( if i have to do something please specify the command i have to enter).
I finally managed to install Mythbuntu but I just cant get the Ir remote control working.
It is a black remote with 4 colored buttons on bottom part (red, green, yellow, blue)
on the box it say model 232 (don't know if it matters)

During the installation the setup asked me what kind of remote it is, there few choices but none that seemed to fit my remote.

Could someone please help me out because I really like to use mythbuntu but without remote it is kind of pointless.

Thank you

---

### Post by ati on 2008-05-01
Usually I don't reply to my own posts but I am just confused now. :confused:
Someone brought to my attention that there are different versions of remote shipped with this card.
My say that it is a Microsoft Certified Remote control. Is that different form the supported one? 
If this remote is not supported please let me know so i can return it and get one that is supported.

---

### Post by bla2000 on 2008-05-02
I don't have a MCE version of the remote. My standard pvr150 remote is working and when I installed I think that there was an option to choose the Hauppauge pvr 150 remote in the list of remotes.

---

### Post by wd5iyt on 2008-05-03
There are several versions of the PVR150 remote.  I have a very early one and it did not work with any of the presets in mythbuntu.  I had to build my own lirc files for the pvr remote.  There are some files for various brands on the lirc.org site that will get you started.  Ditto for my pvr250, which is also an early version.

---

### Post by hihp on 2008-05-03
> **ati said:**
> Hallo,
Hello :-) Are you German or is that "Hallo" a typo? :-)

> I finally managed to install Mythbuntu but I just cant get the Ir remote control working.
It is a black remote with 4 colored buttons on bottom part (red, green, yellow, blue) on the box it say model 232 (don't know if it matters)

During the installation the setup asked me what kind of remote it is, there few choices but none that seemed to fit my remote.
Now, I don't know if the instructions I followed are specific to my IR receiver; from what I understand, they should work with pretty much every IR receiver connected via USB.

The instructions were posted by cjs500 in the [THREAD=723003]Thread "iMON IR and Antec 430 Fusion Knob"[/THREAD].

Let me try to summarize a bit.
**1) Get a shell with root (admin) rights**
For this, enter
```
sudo su
```
and provide your password when queried. Your root prompt should look a bit like this:
```
root@mythtv:~#
```

**2) Check for the presence of the IR receiver**
Query the system to make sure it could actually see the controller for the infrared receiver attached to the USB bus. 
For this, enter
```
lsusb
```
The output you get should look a bit like this:
```
Bus 003 Device 001: ID 0000:0000
Bus 003 Device 004: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c512 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
```
(If you don't use an iMON IR controller, obviously it will say something different, but there should be an infrared controller listed there somewhere.)

**3) Find out the lirc device name**
(This step was not in cjs500's thread, but I imagine this might be helpful.)

Type
```
ls -la /dev/lirc*
```
in order to see a list of all lirc devices; lirc is a program that fetches IR signals from an IR controller and translates them into special "button presses".
Devices are annoted by having a "b" or "c" in the first column of the file permissions:
```
crw-rw---- 1 root root 61, 0 2008-05-03 13:43 /dev/lirc0
srw-rw-rw- 1 root root     0 2008-05-03 13:43 /dev/lircd
```
so /dev/lirc0 is a device (and lircd is not, it is a socket).

If it lists /dev/lirc0, you are good to go. If there are none, your lirc does not seem to be installed; if there are multiple, you might have to try them all out.

**4) Record your infrared remote's different signals**
In this step, you will record all the different buttons on your remote and give each button a name; this information is stored in a file called "lircd.conf". Later you will use these names to do stuff with, so it is a good idea you either write yourself a list or choose names you can remember well so you don't have to look them up in the lircd.conf file that we create now).

Type
```
irrecord --device=/dev/lirc0 /root/lircd.conf
```
That will put the lircd.conf into the root directory where it will be safe :-) Note that if you have multiple IR controllers, you might have to specifiy --device=/dev/lirc1 or --device=/dev/lirc2 or so.

Using irrecord will go like this:
[list]
[*]First irrecord will blurb a bit about itself and ask you to press RETURN to continue.
[*]Then it asks you to hold down an arbitrary button (*any* button will do; keep pressed until irrecord finds a "gap length"). Assuming that the IR device is detected correctly and your remote can communicate properly, you should see dots start streaming across the screen. (cjs500 tried another remote besides the MCE remote and got nothing, so in that case, you have a problem; press Ctrl+C to exit irrecord then.)
[*] The program now goes into button record mode. It goes like this:
[list=1]
[*]it asks you to enter the name for the next button and press enter. You should give the buttons rememberable names, maybe like LiveTV, Ok, Arrow_Up, etc. Don't use spaces in your button labels.
[*]now you press the according button on the remote
[*]irrecord asks you again for a button name. If you have more buttons to to, repeat steps 1 and 2, otherwise just press Enter without typing anything.
[/list]
[*]Lastly, irrecord will ask you to press a button as fast as you can etc. Just follow it until irrecord is satisfied.
[/list]

**5) Backup old lircd.conf and copy in the new one.**
We saved this "master" for reference in the root directory, but we actually need the file somehwere else. We shall make a copy of the old config file just i ncase, and then bring in our new one. Type
```
mv /etc/lirc/lircd.conf /etc/lirc/lircd.conf.old
```
and then
```
cp /root/lircd.conf /etc/lirc/
```

**6) Restart the lirc service**
In order for the new configuration to become effective, the lirc daemon (a daemon is a background service that does helpul things; for example, the MythTV backend also runs as a daemon) needs to be restarted, so type 
```
/etc/init.d/lirc restart
```
You should see output like this:
```
Stopping lirc daemon: lircmd lircd.
Starting lirc daemon: lircd.
```

**7) Test the infrared remote output**
Now we will test if the button presses on the remote are successfully mapped to the "button names" we provided, and thus make sure it's working.

Type
```
irw
```
Once the command executes, press some buttons on your remote and make sure it dumps out codes to the console. If you e.g. pressed the "Play" button, you should see something like:
```
00000000800f0416 00 Play mceusb
00000000800f0416 01 Play mceusb
00000000800f0416 02 Play mceusb
```

**[noparse]8)[/noparse] Map IR buttons to keyboard keypresses**
MythTV is usually controlled by keyboard, i.e. you press buttons in various combinations to achieve things. You can actually change the setup of the buttons, so I would recommend that you do that **first**. Go into the frontend and fiddle around with the setup until you are satisfied. Then write down the combinations you use in a list. For example, in the TV Frontend Playback, you might do this like

PAUSE = SHift+P
PLAY = P
GUIDE = G
CHANNELUP = PgUp
CHANNELDOWN = PgDn

and so forth.

Now we need to create a file called lircrc according to the instructions in chapter [8.4: Additional information for lirc](http://www.mythtv.org/docs/mythtv-HOWTO-8.html#ss8.4) in the MythTV HOW-TO.

The file is located in the directory /home/<front_end_user>/.mythtv/
That means: if for example your user is called "ati", your path would be
```
/home/ati/.mythtv/lircrc
```
Now, use a text editor to edit that file. The order of the buttons does not matter.

For each button, you put in a block of text that looks like this:
```
begin
    remote = mceusb
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end
```
[list]
[*]**remote** specifies for which remote this command is; this is the name that irw outputted above in step 7.
[*]**prog** specifies for which program this mappign is; for example, you could specify button mappings for other programs like firefox, too. Depending on which program is running in the foreground, lirc sends the appropriate keyboard presses to that program.
[*]**button** is one of the button names we assigned in step 4.
[*]**config** is the actual button that should be pressed. This can be a simple key - like "P" for the P key, or "PgDn" for the Page-down key. You can also add qualifiers like the Shift key or the Control key by saying something like "Shift+F6" or "Ctrl+Shift+P".
[/list]

So your file might begin with something like this

```
begin
    remote = mceusb
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Pause
    config = Shift+P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Guide
    config = G
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChannelDown
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChannelUp
    config = PgUp
    repeat = 0
    delay = 0
end
```

I am not sure of at this point you have to restart the computer, just restart the lirc daemon or can just start using the config. Figure that out yourself :-)


Hope that helps.

---

