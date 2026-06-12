---
title: "Official ATI.com drivers, aticonfig explination?"
date: 2006-09-19
forum: Multimedia &amp; Video
---

### Post by stiz on 2006-09-19
I couldnt seem to find this information anywhere (forums, wiki, docs..)
Can someone provide a dumbed down explination of aticonfig settings?  A guide to help people..


**The specific settings I am trying to configure are..**

1. set the exact specs of my monitor
    Scanning-Horizontal Freq   31-95 KHz
    Scanning-Vertical Freq/Refresh    50-120 Hz
    Maximum Resolution Supported  1600 x 1200

2. enable the svideo tv out to display a cloned image of my pc crt monitor, not an extended desktop or anything like that, just a copy of what I see on my computer screen

3. enable 'theater mode' like windows xp drivers that when video is playing on my pc crt monitor it is full screen on my tv, no matter if I have the video minimized or what im doing on my computer screen

4. non ati issue (i think gstreamer?) enable all video in ubuntu to be displayed in hardware overlay mode so that I can see it on my tv screen.

5. hopefully understand tv geometry settings so I can size it properly on my tv

6. when following this guide for official ati driver instalation...[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually")
What do I do when a new kernel update is installed?   Do I follow the whole procedure again from the start (I would think there would be steps to skip doing it a second time or more) ?  


> 
The following command-line options can be invoked as parameters:

ATI Initial Configuration:
  --initial
        Generate a default ATI device section in the configuration file which
        is capable of loading the fglrx driver.
  --initial=dual-head
        Same as '--initial' but generate a basic dual head configuration file.

TV Options:
  --tvf, --tv-format-type=STRING
        Change the TV signal format.  STRING can be one of:
           NTSC-M
           NTSC-JPN
           NTSC-N
           PAL-B
           PAL-COMB-N
           PAL-D
           PAL-G
           PAL-H
           PAL-I
           PAL-K
           PAL-K1
           PAL-L
           PAL-M
           PAL-N
           PAL-SECAM-D
           PAL-SECAM-K
           PAL-SECAM-K1
           PAL-SECAM-L
        Note: Not all graphics cards support every mode. Regional
              settings are applicable.
  --tvs, --tv-standard-type=STRING
        Change the TV standard for TV output.  STRING can be one of:
            VIDEO
            SCART
            YUV
 --tv-overscan={on|off}
       Enable or disable overscan mode for TVout
       Note, not all tv-formats support overscan. Try to
       toggle overscan off before changing tv-format if
       and error occurs.
 --tv-info
         Print out the current tv geometry, tv format, and if the
         tv is physically connected.
 --tv-geometry=WIDTHxHEIGHT{+|-}X{+|-}Y
              =WIDTHxHEIGHT
         Change the size and position of the TVout display.
         WIDTH and HEIGHT are in percentage units. Please note
         that the valid range for WIDTH and HEIGHT depends on
         the tv-format selected. However, as a rule of thumb
         WIDTH and HEIGHT are valid in the range [1,100]
         X and Y are pixels offsets from centre
         of the screen. X and Y are have variable ranges dependant
         on ASIC. Use tv-info to get valid X and Y ranges
         If tv-geometry is invoked with just width and height
         then X and Y are assumed to be 0
         See example 5 below for a sample usage.

FireGL Workstation Board Features:
  --app, --use-app-profile=STRING
        Change the application profile for a FireGL workstation board.
        STRING can be one of:
            default
            maya
            softimage-xsi
            softimage-3d
            houdini4.0
            houdini5.0
            houdini5.5
FSAA Options:
  --fsaa={on|off}
        Enable/disable full scene anti-aliasing.  Enable this option to enhance
        photo-realism in 3D rendering.  Disable it to get the most accurate 3D
        image.
  --fs, --fsaa-samples={off,0,2,4,6}
        Set the number of FSAA samples per pixel or 2, 4, 6.  off is the same
        as setting 0 samples.
  --fsg, --fsaa-gamma={on|off}
        Enable/disable FSAA gamma.
  --fmsp, --fsaa-ms-positions=x0,y0,x1,y1,x2,y2,x3,y3,x4,y4,x5,y5
        Change the FSAA Multi-Sample Positions for x0,y0 to x5,y5.  You must
        specify exactly 12 real number values separated by commas.

Screen-Related Options:
  --ovt, --overlay-type=STRING
        Change the overlay for the X server.  STRING can be one of:
            opengl
            Xv
            disable
  --ovon, --overlay-on={0|1}
        Choose which head the hardware overlay should be visible on.  The
        hardware overlay can be used for either OpenGL, video, pseudo-color
        or stereo.
  --lcd, --lcd-mode=STRING
        Change the LCD mode.  STRING can be one of:
            center
            full
  --dtop, --desktop-setup=STRING
        Change the desktop setup for multiple display adapters.
        STRING can be one of:
            single              1 screen, second dark
            mirror              2 screens - same content, identical
                                refresh rate/resolution
                                Note: This option is NOT supported with Avivo
            clone               2 screens - same content, allows for
                                different refresh rates/resolutions
            horizontal          2 screens - one framebuffer,
                                screen 1 right of screen 0
            horizontal,reverse  2 screens - one framebuffer,
                                screen 1 left of screen 0
            vertical            2 screens - one framebuffer,
                                screen 1 above of screen 0
            vertical,reverse    2 screens - one framebuffer,
                                screen 1 below of screen 0
        Note:  This option is not valid if '--initial=dual-head' is specified.
  --vs, --sync-vsync={on|off}
        Enable/disable sync buffer swaps with vsync.  Enable this option to
        prevent tearing during 3D rendering.
  --psc, --pseudo-color={on|off}
        Enable/disable pseudo-color visuals.  Enable this option to get 16-bit
        color support.
  --stereo={on|off}
        Enable/disable quad-buffer stereo support.  Enable this option only for
        using applications that support the use of hardware 3D shutter glasses.
  --ss, --stereo-sync={on|off}
        Enable/disable quad-buffer stereo sync.  Enable this option to get 3D
        glasses to synchronize with the infrared transmitter.
  --resolution=Screen#,W1xH1,W2xH2,W3xH3,...
        Set the modes for the specified screen.  You may specify several
        resolutions separated by commas.
        Screens start at 0.  You can use 1 for dual-head
  --hsync=Screen#,LOW-HIGH
        Change the horizontal sync range of the specified monitor.  Make sure
        you know the capabilities of your monitor before changing this option.
        Screens start at 0.  You can use 1 for dual-head
  --vrefresh=Screen#,LOW-HIGH
        Change the vertical refresh range of the specified monitor.  Make sure
        you know the capabilities of your monitor before changing this option.
        Screens start at 0.  You can use 1 for dual-head
  --hsync2=LOW-HIGH
        Change the horizontal sync range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --vrefresh2=LOW-HIGH
        Change the vertical refresh range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --mode2=W1xH1,W2XH2,W3xH3,...
        Change the modes for the second display.  You may specify several
        resolutions separated by commas.  Only valid for clone and big desktop
        settings.
  --screen-layout={left|right|above|below}
        Set the secondary screen position for dual head.
  --screen-overlap=NUM
        Set the screen overlap region in big desktop mode to be NUM pixels.
  --force-monitor=STRING[,STRING...]
        Describe all displays that are to be enabled and/or disabled regardless
        of physical connection.  STRING can be one or more of the following
        set, separated by commas:
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            tmds2i
            nocrt1
            nocrt2
            nolvds
            notv
            notmds1
            notmds2
            notmds2i

POWERplay Options:
  Following options will not change the config file.
  These options will be effective immediately. Other options on
  the same command line will be ignored.
  --lsp, --list-powerstates
        Print information about power states and exit.
  --set-powerstate=NUMBER
        Set a power state listed by --list-powerstates.

Advanced Options:
  --tls={on|off}
        Enable/disable fast thread local storage.  Disable this option when
        virtual machines or WineX fail to work properly.
  --sb, --signal-block={on|off}
        Enable/disable signal blocking.  Disable this option when debugging a
        multi-threaded OpenGL application.
  --locked-userpages={on|off}
        Enable/disable locked user pages. Disable this option if the system
        hangs when running fgl_glxgears.
        User page lock is no longer available on AGP system now.
  --gcpu, --generic-cpu={on|off}
        Enable/disable generic CPU.  Use this option if the CPU is being
        reported improperly.  For example: If you have an AMD cpu that is
        being reported as Intel.
  --max-gart-size=NUMBER
        Set user-defined max GART size for non-AGP systems.
        Possible integer values are from 64 to 512 (mb).

Dynamic Display Management Options:
  Following options will not change the config file. They are
  used for querying driver, controller and adaptor information.
  These options will be effective immediately. Other options on
  the same command line will be ignored.
  --enable-monitor=STRING,STRING
        Setting current monitor to be enabled. Only 2 displays
        can be enabled at the same time. Any displays
        that are not on the list will be disabled.
        STRING can be one of the following set, separated
        by commas:
            none
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            auto   -- use default policy to enable the displays.
  --query-monitor
        This will return connected and enabled monitor information
  --swap-monitor
        This only works for big desktop setup. This will swap the
        contents on the two monitors.

Pair mode options:
  Following options are used for query add and remove pair modes.
  These options will be effective immediately. Other options on
  the same command line will be ignored.
  --list-pairmode
        list all the current existing pair modes the driver can use.
  --add-pairmode=width0xheight0+width1xheight1
        Add one pair mode to the list. width0 and height0 are the
        size of primary display and width1 and height1 for the
        secondary  display.
  --remove-pairmode=index
        Remove one pair mode from the list. User can get index by
        list-pairmode.

External Events Daemon Options:
  Following options will not change the config file. They are
  used to send commands to the atieventsd external events daemon.
  --set-policy=STRING
        Sets the event policy for the daemon to be STRING.
        See the atieventsd(8) manpage for further details.

Miscellaneous Options:
  -v, --verbose
        Show what aticonfig is doing.
  -q, --quiet
        Disable all information output except for errors.
  --effective={now,startup}
        Choose when the requested changes should take effect.
            now:     Immediately.  This change will affect the running X
                     session if applicable.  Only 'set-powerstate' and
                     'overlay-on' are applicable for now.
            startup: On future X server startups.  This change will modify the
                     X server configuration file if applicable.
        The default is 'now,startup', i.e., do both as applicable.
  --nobackup
        Do not make an automatic backup of the configuration file.
  -i, --input=FILE
        Select a FILE to input as the configuration file. Set FILE to '-' to
        pipe from standard input.  Without this option, aticonfig will search
        /etc/X11 for the default configuration file.
  -o, --output=FILE
        Select a FILE to output the new configuration file to.  Set FILE to '-'
        to print to standard output.  Without this option, aticonfig will
        replace the input file with the newly generated file.
  -h, --help
        Display this help screen.
  -f, --force
        Only valid with 'initial' option.  Force aticonfig to generate default
        Monitor, Device, and Screen sections even if the original configuration
        file has invalid settings in these sections.

Examples:
  1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
       Dual head   :    aticonfig --initial=dual-head --screen-layout=above
                        This command will generate a dual head configuration
                        file with the second screen located above the first
                        screen.
  2. Setting up big desktop to horizontal and set overlay on secondary display.
                        aticonfig --dtop=horizontal --overlay-on=1
  3. Setting up modes for primary display.
                        aticonfig --resolution=0,1600x1200,1280x1024,1024x768
  4. Force primary CRT on and TV-out off.
                        aticonfig --force-monitor=crt1,notv
  5. Change tv geometry
                         aticonfig --tv-geometry=85x90+10-10
         This will set tv to 85% width (where 100% ==
         overscan) 90% height and shift 10 pixels right of centre
         and 10 pixels down of centre.



Thank You for listening

---

### Post by stiz on 2006-09-20
bump :D

---

### Post by whatever on 2006-09-20
> **stiz said:**
> 6. when following this guide for official ati driver instalation...[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually")
What do I do when a new kernel update is installed?   Do I follow the whole procedure again from the start (I would think there would be steps to skip doing it a second time or more) ?

it should be enough to repeat the "module-assistant" commands only.

---

### Post by stiz on 2006-09-21
bump :)

---

### Post by stiz on 2006-09-23
bump again

---

