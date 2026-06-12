---
title: "LIRC for Compro VIdeoMate TV PVR - Resources to set it up"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by ariel on 2007-12-08
After a bit of pain I got the remote of my Compro VideoMate TV PVR card (based on SAA7134) to work with Totem, VLC and gmplayer, and also to shutdown the machine from the remote.

The files "lircd.conf" and ".lircrc" are specific for the remote control that comes with this Compro card; however they may still be useful to you to easily see the totem/vlc/mplayer lirc commands.

Here I just list the resources I found particularly useful and attach my final 
config files.  This *might* save you some time & effort. 


 > Remote (using Compro VideoMate TV PVR - chipset SAA7134)

    Check that the SAA71xx modules are loaded (7.10 should load them automatically): lsmod |grep saa

   Install LIRC from the repos:

    sudo apt-get install lirc lirc-modules-source module-assistant
      (Driver selection: not important, we will change it later; example: choose Avermedia (card=13))

    Now we need to obtain the DEVICE to use in /etc/lirc/hardware.conf:

    cat /proc/bus/input/devices

      Check output for the event name:     H: Handlers=kbd event4 
      In my case is event4;
      Thus I will use: DEVICE="/dev/input/event4"  in hardware.conf

    SAA7134 IR buttons are seen by lircd through the linux input layer (like if it were a keyboard)
    This means the in hardware.conf we need the driver line to look lie:
     DRIVER="dev/input"

     Save /etc/lirc/hardware.conf with the new configuration.

     Download my config file, and place lircd.conf in your /etc/lirc folder, and ".lircrc" (note the dot in front) in your home folder (/home/your_username).

     Now reload the daemon so that it it takes the new config: 

     sudo /etc/init.d/lirc restart

     Now let's check that the remote is working:

     We use the command "irw" for this, launch it in a terminal and press a few buttons, you should see something like:

         0000000000010067 00 UP linux-input-layer
         0000000000010069 00 LEFT linux-input-layer
         Otherwise lircd was started with the wrong driver or device
          

    VLC LIRC: 
       - Activation: settings > preferences > interfaces > control interfaces > infrared remote
       - should work out of the box after the LIRC activation in vlc with my ".lircrc" file; if you want to tweak the config see below
       - vlc --longhelp |grep key
       - full list of vlc lirc commands: [http://wiki.videolan.org/How_to_Use_Lirc](http://wiki.videolan.org/How_to_Use_Lirc)

    Totem LIRC commands: 
       - Activation: edit > plugins > "infrared remote control"
       - should work out of the box after the LIRC activation with my ".lircrc" file; if you want to tweak the config see below
       - full list: [http://gentoo-wiki.com/HOWTO_LIRC#Using_LIRC_with_totem](http://gentoo-wiki.com/HOWTO_LIRC#Using_LIRC_with_totem)
       - the above is a bit outdated; check as well: totem --help

    Mplayer (and gmplayer) LIRC commands: 
       - Activation: it's on by default
       - should work out of the box with my ".lircrc" file; if you want to tweak the config see below
       - full list of lirc commands: mplayer -input cmdlist


    To suspend/shutdown with the remote:
    - Start the irexec daemon on boot (System > Preferences > Sessions); 
    - then in ~/.lircrc  add this:
       begin
         prog = irexec
         button = <YOUR CHOSEN SUSPEND BUTTON>
         config = /etc/acpi/sleep.sh
       end

---

### Post by ov1d1u on 2008-04-12
Thank you very much! It worked for me :) I have just a question: In KDE, when I press the remote control's volume keys, it show a little window with a progress bar and a text "Volume", but when I push Volume- key the sound doesn't change his volume (but in that window the progress bar reacts to my commands). Any idea to solve this? (I think the Master Channel is wrong selected, bu in KMix is correctly seted). Thanks.

---

### Post by ariel on 2008-04-13
you are welcome.

In LIRC, each application has to "subscribe" to the LIRC service, usually via plugins. This is regardless of whether the application is gnome or kde. 

Thus you have plugins (or the like) for audacious, VLC, Elisa, amarok, whatever.

From what you say it seems that KDE's audio mixer app has a LIRC plugin, it is active, and your ".lircrc" is somehow handling it. 

You will need to find kmix (or whatever the app is) documentation, and look at the LIRC section, where they should specify the commands they can accept via LIRC; then go to ".lircrc", find the section for that application, and map the remote keys to the apps functions the way you like the most.

hope this helps,
cheers
a

ps. this works in Hardy / 8.04 as well. However hardy has a kernel issue with the SAA7134 chipset that the tv tuner card uses, audio part, it may get fixed before launch. In any case there is a simple workaround here:

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271)

---

