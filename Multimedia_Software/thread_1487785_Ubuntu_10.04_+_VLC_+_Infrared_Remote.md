---
title: "Ubuntu 10.04 + VLC + Infrared Remote"
date: 2010-05-19
forum: Multimedia Software
---

### Post by SupaRice on 2010-05-19
I've got an HP Pavillion dv9000 laptop, the type that come with an HDMI port and a built in Windows media center remote.

How do I make it work with VLC?

I've done a little research, and I've installed lirc. It now sorta works with Totem, but not at all with VLC.  What am I doing wrong?

---

### Post by SupaRice on 2010-05-24
Nobody?

---

### Post by LarryJ2 on 2010-06-27
Did you try   starting  VLC as
vlc -I lirc

Not certain that will help but it solved my problem with a USB MCE USB Remote

---

### Post by vfiz on 2010-06-27
I believe you have to set up a configuration file (~/.lircrc) specifically for VLC.  The lircrc file (detailed at [http://www.lirc.org/html/configure.html]("http://www.lirc.org/html/configure.html"), scroll down toward the bottom) basically takes the input from your remote and translates it into a command for a specific program.  Although it's for Gentoo Linux, this little wiki article should work well: [http://en.gentoo-wiki.com/wiki/VLC/LIRC]("http://en.gentoo-wiki.com/wiki/VLC/LIRC").

In order to use lirc with VLC, you've also got to tell VLC to do so.  I haven't done anything in VLC from the command line, so what the previous poster put may work.  You can also open VLC and do it graphically.  Click on Tools > Preferences.  Then, at the preferences screen, click on the All radio button under Show Settings at the bottom.  When you get to the "all settings" view, click on the + by Interface, and then click on Control Interfaces (not the plus sign).  There is a check box for Infrared Remote Control Interface.  Click that and save the changes.

There's also an Infrared category if you expand Control Interfaces, where you can specify the lirc configuration file.

---

### Post by tzily on 2010-07-26
I give up. Tried to make this work but nothing.
Installed lirc and configured my RC6 hp remote in the terminal selecting the windows media center one from the list. Then tried some combinations in vlc, then tried starting it using vlc -I lirc and it sent me to a different config here /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb (also tried changing both configuration locations in /etc and here in the vlc settings)  ... edited that file and error changed to

VLC media player 1.1.0 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x97dab24] lirc interface error: lirc initialisation failed
[0x97dab24] main interface error: no suitable interface module
[0x97b267c] main libvlc error: interface "default" initialization failed

I'm sure it's not configured right, but maybe i'm too dumb for this and i don't have the nerves right now to try harder.

Here's the original error:

tzily@PC:~$ vlc -I lirc
VLC media player 1.1.0 The Luggage (revision exported)
vlc: unknown token "name" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:38 ignored
vlc: unknown token "bits" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:39 ignored
vlc: unknown token "flags" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:40 ignored
vlc: unknown token "eps" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:41 ignored
vlc: unknown token "aeps" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:42 ignored
vlc: unexpected token in line /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:44
vlc: unexpected token in line /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:45
vlc: unexpected token in line /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:46
vlc: unknown token "pre_data_bits" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:47 ignored
vlc: unknown token "pre_data" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:48 ignored
vlc: unknown token "gap" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:49 ignored
vlc: unknown token "toggle_bit" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:50 ignored
vlc: unknown token "rc6_mask" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:51 ignored
vlc: bad file format, /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:54
[0xa06ddec] lirc interface error: failure while reading lirc config
[0xa06ddec] main interface error: no suitable interface module
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
vlc: unknown token "name" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:38 ignored
vlc: unknown token "bits" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:39 ignored
vlc: unknown token "flags" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:40 ignored
vlc: unknown token "eps" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:41 ignored
vlc: unknown token "aeps" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:42 ignored
vlc: unexpected token in line /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:44
vlc: unexpected token in line /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:45
vlc: unexpected token in line /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:46
vlc: unknown token "pre_data_bits" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:47 ignored
vlc: unknown token "pre_data" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:48 ignored
vlc: unknown token "gap" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:49 ignored
vlc: unknown token "toggle_bit" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:50 ignored
vlc: unknown token "rc6_mask" in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:51 ignored
vlc: bad file format, /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb:54
[0xa06da8c] lirc interface error: failure while reading lirc config
[0xa06da8c] main interface error: no suitable interface module
[0xa04467c] main libvlc error: interface "default" initialization failed

---

### Post by digbysellers on 2010-07-29
I installed mythbuntu-lirc-generator on my 10.04 box (not mythbuntu) and removed vlc 1.0.6. I followed some instructions elsewhere (I am no expert) to install vlc 1.1.1 which has the option to specify where it looks for lirc files. Play, pause and stop seem to work. I have yet to get my head around the configuring the rest in .lirc/ 
Just getting this far by myself and some other people forum requests for help had me frazzled.  

I should mention that I'm using a streamzap remote, but from what I've read the hardware is much of a muchness once you have it working with "irw" terminal command test. 

I've been putting this off for a while and now I remember why. I still prefer this to messing around with it in xp. Though just barely.

---

### Post by digbysellers on 2010-07-29
I should also mention that I don't have to start vlc 1.1.1 now with any special commands, those remote functions seem to always be functional.

---

### Post by dleite on 2010-08-30
> **SupaRice said:**
> I've got an HP Pavillion dv9000 laptop, the type that come with an HDMI port and a built in Windows media center remote.

How do I make it work with VLC?

I've done a little research, and I've installed lirc. It now sorta works with Totem, but not at all with VLC.  What am I doing wrong?

I finally got my Ubuntu 10.04 working with XBMC and VLC with a XBOX remote and dongle. With XBMC and VLC I have successfully remapped my buttons to how I want them. I followed this and replaced the files as necessarry. This was the only thing I was able to get XBOX remote to work in Ubuntu 10.04 after 2 weeks of trying, 

[http://lincudo.org/index.php?name=News&file=article&sid=74](http://lincudo.org/index.php?name=News&file=article&sid=74)

First, you need to install and configure *LIRC. *I found it useful in Terminal to make sure LIRC successfully. In Terminal run /etc/init.d/lirc restart and you will see this. I found that if LIRC failed then it was hit/miss if the remote would work in XBMC or VLC.

root@finn123-desktop:/etc/lirc# /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ]


After you install LIRC and the remote, from the Terminal run IRW. Press your remote buttons, you should see something like this: 

root@finn123-desktop:/etc/lirc# irw
00000000000000a8 00 RIGHT XboxDVDDongle
00000000000000a8 01 RIGHT XboxDVDDongle
00000000000000a9 00 LEFT XboxDVDDongle
00000000000000a6 00 UP XboxDVDDongle
00000000000000e0 00 STOP XboxDVDDongle
00000000000000e0 01 STOP XboxDVDDongle
00000000000000e3 00 FORWARD XboxDVDDongle
00000000000000e3 01 FORWARD XboxDVDDongle
00000000000000e3 02 FORWARD XboxDVDDongle
00000000000000c6 00 VOL+ XboxDVDDongle
00000000000000c6 01 VOL+ XboxDVDDongle
00000000000000c8 00 VOL- XboxDVDDongle
00000000000000c8 00 VOL- XboxDVDDongle
00000000000000c8 01 VOL- XboxDVDDongle

For VLC, here is my .lircrc file (located in /home/**Username/ and I just pointed to VLC to use this file) Note I can now use my XBOX remote to make VLC fullscreen and with volume control. Pause function is now *key-play-pause*:

### VLC ###
###
begin vlc
    # play
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = PLAY
        repeat = 0
        config = key-play-pause
    end
    # stop
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = STOP
        repeat = 0
        config = key-stop
    end
    # pause
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = PAUSE
        repeat = 0
        config = key-play-pause
    end
    # up
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = UP
        repeat = 0
        config = key-nav-up
    end
    # down
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = DOWN
        repeat = 0
        config = key-nav-down
    end
    # left
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = LEFT
        repeat = 0
        config = key-nav-left
    end
    # right
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = RIGHT
        repeat = 0
        config = key-nav-right
    end
    # select
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = SELECT
        repeat = 0
        config = key-nav-activate
    end
    # forward
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = FORWARD
        repeat = 3
        config = key-jump+medium
    end
    # rewind
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = REVERSE
        repeat = 3
        config = key-jump-short
    end
    # menu
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = TITLE
        repeat = 0
        config = key-disc-menu
    end
    # next chapter
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = SKIP+
        repeat = 3
        config = key-chapter-next
    end
    # previous chapter
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = SKIP-
        repeat = 3
        config = key-chapter-prev
    end
    # fullscreen
    begin
        remote = XboxDVDDongle
        prog = vlc
        button = DISPLAY
        repeat = 0
        config = key-toggle-fullscreen
    end

    begin
        prog = vlc
        button = VOL+
        config = key-vol-up
        repeat = 1
    end
    begin
        prog = vlc
        button = VOL-
        config = key-vol-down
        repeat = 1
    end
    begin
        prog = vlc
        button = MUTE
        config = key-vol-mute
        repeat = 0
    end
end vlc


In VLC, enable Infrared Remote. Restart VLC, restart LIRC and it should be good.

Let us know how it goes. I've been working on my remote for a month now and finally got everything how I want it.

---

