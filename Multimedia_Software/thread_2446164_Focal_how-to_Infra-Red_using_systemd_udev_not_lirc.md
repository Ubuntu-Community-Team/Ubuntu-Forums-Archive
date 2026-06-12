---
title: "Focal how-to Infra-Red using systemd udev not lirc"
date: 2020-06-25
forum: Multimedia Software
---

### Post by vidtek on 2020-06-25
[B][SIZE=4]Now lirc is almost defunct it is time to get to grips with the systemd way of handling ir remotes.
[/SIZE][/B]
It turns out to be remarkably easy.  First purge all traces of lirc!  Purge purge and purge again.  Lirc is lurking in the dark corners of your system somewhere!

For a bog standard mce clone remote these are the steps:

1) locate your remote file template it is in [COLOR="#008000"]/lib/udev/rc_keymaps[/COLOR]  it is [COLOR="#FF0000"]rc6_mce.toml
[/COLOR]
2) copy it from [COLOR="#008000"]/lib/udev/rc_keymaps[/COLOR]  to [COLOR="#008000"]/etc/rc_keymaps[/COLOR] # ```
sudo cp /lib/udev/rc_keymaps/rc6_mce.toml /etc/keymaps
```  

3)  ** EDIT: 12 Jan 2021---- Since writing this the devs have changed things a bit--you now need to leave the suffix .toml on your file!!!!**

4)  Install ir-keytable 

	```
sudo apt install ir-keytable
```

5) check it works by pressing a few keys on your remote:

	```
sudo ir-keytable -t
```

	You should see scancodes appear on the screen like this:```
root@linuxmint:/home/tony# ir-keytable -t
Testing events. Please, press CTRL-C to abort.
35910.869695: lirc protocol(rc6_mce): scancode = 0x800f0422
35910.869728: event type EV_MSC(0x04): scancode = 0x800f0422
35910.869728: event type EV_KEY(0x01) key_down: KEY_ENTER(0x001c)
35910.869728: event type EV_SYN(0x00).

35910.973709: lirc protocol(rc6_mce): scancode = 0x800f0422
35910.973740: event type EV_MSC(0x04): scancode = 0x800f0422
35910.973740: event type EV_SYN(0x00).
35911.085677: lirc protocol(rc6_mce): scancode = 0x800f0422
35911.085708: event type EV_MSC(0x04): scancode = 0x800f0422
35911.085708: event type EV_SYN(0x00).
35911.261904: event type EV_KEY(0x01) key_up: KEY_ENTER(0x001c)
35911.261904: event type EV_SYN(0x00).
35915.101985: lirc protocol(rc6_mce): scancode = 0x800f0426
35915.102017: event type EV_MSC(0x04): scancode = 0x800f0426
35915.102017: event type EV_KEY(0x01) key_down: KEY_S(0x001f)
35915.102017: event type EV_SYN(0x00).
s35915.205961: lirc protocol(rc6_mce): scancode = 0x800f0426
35915.205996: event type EV_MSC(0x04): scancode = 0x800f0426
35915.205996: event type EV_SYN(0x00).
35915.309934: lirc protocol(rc6_mce): scancode = 0x800f0426
35915.309953: event type EV_MSC(0x04): scancode = 0x800f0426
35915.309953: event type EV_SYN(0x00).
35915.489891: event type EV_KEY(0x01) key_up: KEY_S(0x001f)
35915.489891: event type EV_SYN(0x00).
35918.462170: lirc protocol(rc6_mce): scancode = 0x800f0416 toggle=1
35918.462209: event type EV_MSC(0x04): scancode = 0x800f0416
35918.462209: event type EV_KEY(0x01) key_down: KEY_P(0x0019)
35918.462209: event type EV_SYN(0x00).
p35918.566214: lirc protocol(rc6_mce): scancode = 0x800f0416 toggle=1
35918.566243: event type EV_MSC(0x04): scancode = 0x800f0416
35918.566243: event type EV_SYN(0x00).
35918.678191: lirc protocol(rc6_mce): scancode = 0x800f0416 toggle=1
35918.678220: event type EV_MSC(0x04): scancode = 0x800f0416
35918.678220: event type EV_SYN(0x00).
35918.857917: event type EV_KEY(0x01) key_up: KEY_P(0x0019)
35918.857917: event type EV_SYN(0x00).


```

6) run this command to activate the new configuration [COLOR="#FF0000"](must be done after every change)
[/COLOR]
	```
sudo ir-keytable -c -w /etc/rc_keymaps/rc6_mce.toml

```


7) set up your favourite text editor in a window on the right of the screen and have that file open at the same time as running an  		instance of mythtv in a window on the left with the key editor open. 

	```
mythfrontend -geometry 1280x900
```
 
8) modify ONLY the text next to KEY_??? to reflect what mythtv has mapped to the key you want.

	eg. the existing line:- scancode 0x800f040a = [COLOR="#0000FF"]KEY_DELETE [/COLOR](0x6f)

	change to scancode 0x800f040a = [COLOR="#0000FF"]KEY_D[/COLOR] (0x6f)  #was DELETE

	I always make a note of the original so I don't get too confused when I need to change things.

9) After making your changes, save the rc6_mce.toml file open in the text editor, save any changes to your mythtv keymappings and 
run the command in (no 6) and logoff to close the x system.  I just reboot - it is easier.

In my humble opinion this is far superior to the dogs breakfast that lirc has become.

Cheers, Tony

EDIT-2nd July 2020-----I have found when starting the udev rule does not always kick in at boot
EDIT-20Jan 2021  The following is a much more elegant fix for the boot issue using a text editor create a rule file called[COLOR="#FF0000"] ir-keytable.service[/COLOR]: 


```
[Unit]
Description=ensure IR remote codes are activated at boot 

[Service]
Type=oneshot
ExecStart=/usr/bin/ir-keytable -c -w /etc/rc_keymaps/rc6_mce.toml
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```

Place this in your /etc/systemd/system directory.
Then: ```
sudo systemctl enable ir-keytable.service
and
sudo systemctl start ir-keytable.service
```


Tony.

EDIT 20th Aug 2020.............

For those with set-top boxes that require an ir-blaster, ir-keytable is not lirc!  To use a blaster you need to create a mythtv job with the correct keyboard scankeycodes to run your set top box.  Check here for your set-top box codes: /lib/udev/rc_keymaps.

I do not use a blaster, if anyone has a sample job please post it here.


Cheers Tony

---

### Post by robbrown2 on 2021-04-26
Hi All.


I have a weird problem that I have been struggling with for a few months on and off.


I followed the steps to get ir-keytable installed (and as I installed a minimal 20.04, Lirc wasn't installed - although I checked).


So, when running sudo ir-keytable -t, I get a scan code come up and a match for the button (such as KEY-ENTER) BUT it gets stuck and continually streams out the same code. If I press another button, the stream of text changes to the correct button pressed (say KEY-RIGHT) and never stops streaming. To explain it, exactly like if I was holding the button (or pressing and holding a key on the keyboard).


Here is an example:
```
sudo ir-keytable -t
Testing events. Please, press CTRL-C to abort.
306.343162: lirc protocol(rc6_mce): scancode = 0x800ff422 toggle=1
306.343173: event type EV_MSC(0x04): scancode = 0x800ff422
306.343173: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
306.343173: event type EV_SYN(0x00).
306.447158: lirc protocol(rc6_mce): scancode = 0x800ff422 toggle=1
306.447166: event type EV_MSC(0x04): scancode = 0x800ff422
306.447166: event type EV_SYN(0x00).
306.559153: lirc protocol(rc6_mce): scancode = 0x800ff422 toggle=1
306.559163: event type EV_MSC(0x04): scancode = 0x800ff422
306.559163: event type EV_SYN(0x00).
306.866743: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
306.866743: event type EV_SYN(0x00).
306.998738: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
306.998738: event type EV_SYN(0x00).
307.130743: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.130743: event type EV_SYN(0x00).
307.262745: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.262745: event type EV_SYN(0x00).
307.394748: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.394748: event type EV_SYN(0x00).
307.526747: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.526747: event type EV_SYN(0x00).
307.658743: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.658743: event type EV_SYN(0x00).
307.790758: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.790758: event type EV_SYN(0x00).
307.922732: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.922732: event type EV_SYN(0x00).
308.054755: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
308.054755: event type EV_SYN(0x00).
308.186744: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
308.186744: event type EV_SYN(0x00).
308.318734: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
308.318734: event type EV_SYN(0x00).
308.450727: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
308.450727: event type EV_SYN(0x00).
^C

```


At first I thought the remote was doing it, but it isn't (I made sure remote was not sending IR by looking at the IR Leds through the phone camera and took the remote out of the room).


It is like a buffer is not getting cleared or something thinks the IR signal is still being received.


I played with the repeat delay and repeat period but still did the same with any values


```
sudo ir-keytable -D 500 -P 125
```


Running the command sudo ir-keytable returns the following:


{CODE]sudo ir-keytable
Found /sys/class/rc/rc0/ with:
        Name: iMON Remote (15c2:ffdc)
        Driver: imon
        Default keymap: rc-imon-mce
        Input device: /dev/input/event5
        LIRC device: /dev/lirc0
        Supported kernel protocols: rc-6
        Enabled kernel protocols: rc-6
        bus: 3, vendor/product: 15c2:ffdc, version: 0x0000
        Repeat delay = 500 ms, repeat period = 125 ms
[/CODE]

I'm not sure what to look at to see why this repeating is occurring.

Any ideas?

Thanks...

---

### Post by vidtek on 2021-04-26
> **robbrown2 said:**
> Hi All.


I have a weird problem that I have been struggling with for a few months on and off.


I followed the steps to get ir-keytable installed (and as I installed a minimal 20.04, Lirc wasn't installed - although I checked).


So, when running sudo ir-keytable -t, I get a scan code come up and a match for the button (such as KEY-ENTER) BUT it gets stuck and continually streams out the same code. If I press another button, the stream of text changes to the correct button pressed (say KEY-RIGHT) and never stops streaming. To explain it, exactly like if I was holding the button (or pressing and holding a key on the keyboard).


Here is an example:
```
sudo ir-keytable -t
Testing events. Please, press CTRL-C to abort.
306.343162: lirc protocol(rc6_mce): scancode = 0x800ff422 toggle=1
306.343173: event type EV_MSC(0x04): scancode = 0x800ff422
306.343173: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
306.343173: event type EV_SYN(0x00).
306.447158: lirc protocol(rc6_mce): scancode = 0x800ff422 toggle=1
306.447166: event type EV_MSC(0x04): scancode = 0x800ff422
306.447166: event type EV_SYN(0x00).
306.559153: lirc protocol(rc6_mce): scancode = 0x800ff422 toggle=1
306.559163: event type EV_MSC(0x04): scancode = 0x800ff422
306.559163: event type EV_SYN(0x00).
306.866743: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
306.866743: event type EV_SYN(0x00).
306.998738: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
306.998738: event type EV_SYN(0x00).
307.130743: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.130743: event type EV_SYN(0x00).
307.262745: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.262745: event type EV_SYN(0x00).
307.394748: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.394748: event type EV_SYN(0x00).
307.526747: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.526747: event type EV_SYN(0x00).
307.658743: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.658743: event type EV_SYN(0x00).
307.790758: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.790758: event type EV_SYN(0x00).
307.922732: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
307.922732: event type EV_SYN(0x00).
308.054755: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
308.054755: event type EV_SYN(0x00).
308.186744: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
308.186744: event type EV_SYN(0x00).
308.318734: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
308.318734: event type EV_SYN(0x00).
308.450727: event type EV_KEY(0x01) key_down: KEY_OK(0x0160)
308.450727: event type EV_SYN(0x00).
^C

```


At first I thought the remote was doing it, but it isn't (I made sure remote was not sending IR by looking at the IR Leds through the phone camera and took the remote out of the room).


It is like a buffer is not getting cleared or something thinks the IR signal is still being received.


I played with the repeat delay and repeat period but still did the same with any values


```
sudo ir-keytable -D 500 -P 125
```


Running the command sudo ir-keytable returns the following:


{CODE]sudo ir-keytable
Found /sys/class/rc/rc0/ with:
        Name: iMON Remote (15c2:ffdc)
        Driver: imon
        Default keymap: rc-imon-mce
        Input device: /dev/input/event5
        LIRC device: /dev/lirc0
        Supported kernel protocols: rc-6
        Enabled kernel protocols: rc-6
        bus: 3, vendor/product: 15c2:ffdc, version: 0x0000
        Repeat delay = 500 ms, repeat period = 125 ms
[/CODE]

I'm not sure what to look at to see why this repeating is occurring.

Any ideas?

Thanks...
Rob-  I had exactly the same problem as you describe and it too drove me nuts.  In the end I gave up and did a total re-install from scratch.   I now use KDE neon focal instead of greedy, and have found it to be much more stable than almost any other distro with mythtv.

It happened for me after a massive update and I was never able to track down the source of the problem.

You haven't put what distro you are using.  The best way without having to keep repeatedly putting your system information into posts is to create your signature and put it there.  That way everyone who can help is able to see it when you post for assistance.  Check out the bottom of my post.

---

### Post by vidtek on 2021-04-26
Rob- This is my result:

```
root@linuxmint:/home/tony# ir-keytable -t
Testing events. Please, press CTRL-C to abort.
66363.854181: lirc protocol(rc6_mce): scancode = 0x800f0422 toggle=1
66363.854207: event type EV_MSC(0x04): scancode = 0x800f0422
66363.854207: event type EV_KEY(0x01) key_down: KEY_ENTER(0x001c)
66363.854207: event type EV_SYN(0x00).

66363.958168: lirc protocol(rc6_mce): scancode = 0x800f0422 toggle=1
66363.958173: event type EV_MSC(0x04): scancode = 0x800f0422
66363.958173: event type EV_SYN(0x00).
66364.062187: lirc protocol(rc6_mce): scancode = 0x800f0422 toggle=1
66364.062202: event type EV_MSC(0x04): scancode = 0x800f0422
66364.062202: event type EV_SYN(0x00).
66364.199298: event type EV_KEY(0x01) key_up: KEY_ENTER(0x001c)
66364.199298: event type EV_SYN(0x00).
66369.542440: lirc protocol(rc6_mce): scancode = 0x800f0418
66369.542476: event type EV_MSC(0x04): scancode = 0x800f0418
66369.542476: event type EV_KEY(0x01) key_down: KEY_PAUSE(0x0077)
66369.542476: event type EV_SYN(0x00).
66369.646479: lirc protocol(rc6_mce): scancode = 0x800f0418
66369.646502: event type EV_MSC(0x04): scancode = 0x800f0418
66369.646502: event type EV_SYN(0x00).
66369.750495: lirc protocol(rc6_mce): scancode = 0x800f0418
66369.750507: event type EV_MSC(0x04): scancode = 0x800f0418
66369.750507: event type EV_SYN(0x00).
66369.883283: event type EV_KEY(0x01) key_up: KEY_PAUSE(0x0077)
66369.883283: event type EV_SYN(0x00).
66373.390646: lirc protocol(rc6_mce): scancode = 0x800f0416 toggle=1
66373.390674: event type EV_MSC(0x04): scancode = 0x800f0416
66373.390674: event type EV_KEY(0x01) key_down: KEY_PLAY(0x00cf)
66373.390674: event type EV_SYN(0x00).
66373.494624: lirc protocol(rc6_mce): scancode = 0x800f0416 toggle=1
66373.494645: event type EV_MSC(0x04): scancode = 0x800f0416
66373.494645: event type EV_SYN(0x00).
66373.606664: lirc protocol(rc6_mce): scancode = 0x800f0416 toggle=1
66373.606686: event type EV_MSC(0x04): scancode = 0x800f0416
66373.606686: event type EV_SYN(0x00).
66373.739246: event type EV_KEY(0x01) key_up: KEY_PLAY(0x00cf)
66373.739246: event type EV_SYN(0x00).
```


and:

```
root@linuxmint:/home/tony# ir-keytable
Found /sys/class/rc/rc0/ with:
        Name: Media Center Ed. eHome Infrared Remote Transceiver (1784:0008)
        Driver: mceusb
        Default keymap: rc-rc6-mce
        Input device: /dev/input/event9
        LIRC device: /dev/lirc0
        Attached BPF protocols: Operation not supported
        Supported kernel protocols: lirc rc-5 rc-5-sz jvc sony nec sanyo mce_kbd rc-6 sharp xmp imon rc-mm 
        Enabled kernel protocols: lirc rc-6 
        bus: 3, vendor/product: 1784:0008, version: 0x0100
        Repeat delay = 500 ms, repeat period = 125 ms

```

Hope this helps.  I have a rather complicated ir setup, I live in a granny flat and my computers live in the loft above with an ir-extender to my computer and HTPC amplifier .  I too looked first at hardware problems, but on restoring an old backup the issue disappeared.  It is definitely kernel related, but what it is I have no idea.

Tony.

---

### Post by robbrown2 on 2021-04-26
> **vidtek said:**
> Rob-  I had exactly the same problem as you describe and it too drove me nuts.  In the end I gave up and did a total re-install from scratch.   I now use KDE neon focal instead of greedy, and have found it to be much more stable than almost any other distro with mythtv.

It happened for me after a massive update and I was never able to track down the source of the problem.

You haven't put what distro you are using.  The best way without having to keep repeatedly putting your system information into posts is to create your signature and put it there.  That way everyone who can help is able to see it when you post for assistance.  Check out the bottom of my post.

Hi Tony, Thanks for the reply... Sorry about not mentioning the distro.. I'm using Ubunutu 20.04.01 LTS at present.

Unfortunately, this is a brand new build from scratch.

What is really weird, is that I have another SSD with (ubuntu 20.04.01) and it is working perfectly, with the same configuration, however, something is a miss with the OS as it starts OK, runs Kodi OK, but I cannot bring up the terminal or most other software such as Software Updater, Applications, etc... It seems to just sit there with the wait cursor, then that disappears. I think it has something to do with any application that uses Python is a problem (except Kodi).

I thought I will just do the new fresh install on another SSD (have plenty lying around) just in case I needed to go back.

After the fresh install, I started installing the hardware (I have a system with Soundgraph IMON VFD and IR), then started trying the remote and this is where I got to. I have all my install documented from last time I got this working... Maybe I have missed some config for the LCDd config for the Soundgraph.

I might try another fresh install but with an older version like 18.04 (although I know it has its problems too)... Or give KDE Neon a try (although it seems to be based on Ubunutu 20.04 now)...

Thanks,
Rob

---

### Post by robbrown2 on 2021-04-27
Just an update...

Installed KDE Neon and it worked perfectly from the get go. Although based on Ubuntu 20.04, it seems to run a whole lot faster too.

Thanks.

---

### Post by vidtek on 2021-04-27
> **robbrown2 said:**
> Just an update...

Installed KDE Neon and it worked perfectly from the get go. Although based on Ubuntu 20.04, it seems to run a whole lot faster too.

Thanks.

It's a pretty minimal install but I find it installs seamlessly and runs well with Mythtv.  There is a routine I now use for installs and it only takes me a day to get everything up and running including Mythtv.   I have never been able to get Kodi to work properly, but Mythtv does everything I need.  With a basic install saved by qt-fsarchiver with mythtv installed in that backup I can be up and running in under 30 mins now with all my defaults.  

BEWARE--if you have a Nvidia card do not install updates or update your nvidia driver.   There is still a bug which hangs the boot for over a minute on the i2c bus.

Cheers Tony

---

### Post by robbrown2 on 2021-04-27
> **vidtek said:**
> It's a pretty minimal install but I find it installs seamlessly and runs well with Mythtv.  There is a routine I now use for installs and it only takes me a day to get everything up and running including Mythtv.   I have never been able to get Kodi to work properly, but Mythtv does everything I need.  With a basic install saved by qt-fsarchiver with mythtv installed in that backup I can be up and running in under 30 mins now with all my defaults.  

BEWARE--if you have a Nvidia card do not install updates or update your nvidia driver.   There is still a bug which hangs the boot for over a minute on the i2c bus.

Cheers Tony

Hey Tony, thanks for the extra info. My Kodi (v19) is running fine (atm). Thanks for the tip on the qt-fsarchiver option. I was thinking I need to create an image once I have completed.. Yes, I have an Nvidia card, so will have to keep an eye on that.

Thanks again.
Rob

---

### Post by flychen on 2021-06-12
> **vidtek said:**
> Rob-  I had exactly the same problem as you describe and it too drove me nuts.  In the end I gave up and did a total re-install from scratch.   I now use KDE neon focal instead of greedy, and have found it to be much more stable than almost any other distro with mythtv.

It happened for me after a massive update and I was never able to track down the source of the problem.

You haven't put what distro you are using.  The best way without having to keep repeatedly putting your system information into posts is to create your signature and put it there.  That way everyone who can help is able to see it when you post for assistance.  Check out the bottom of my post.
This problem is a driver bug described here: [https://www.spinics.net/lists/stable/msg441113.html](https://www.spinics.net/lists/stable/msg441113.html)

---

