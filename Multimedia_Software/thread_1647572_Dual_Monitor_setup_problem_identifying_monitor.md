---
title: "Dual Monitor setup problem identifying monitor"
date: 2010-12-17
forum: Multimedia Software
---

### Post by complience on 2010-12-17
I am trying to setup Dual monitors with individual (non-mirrored) desktops.

AMDCCCLE will only identify the monitor I want to use as primary as number 2 and the monitor I want to use as secondary
as number 1 - I have tasksbars, awm, desktop items configured to use the first screen and the second screen is clear for media use.

The choice seems to be determined by what output port on my graphic card.. whatever monitor is attached to the HDMI port is called 1. 

xrandr can only identify the 2nd monitor - the first monitor is unknown

I've attached my xorg.conf

---

### Post by complience on 2010-12-17
xorg.conf

> **complience said:**
> Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1360x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1360x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-DFP2" "0-DFP2"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual   3280 1080
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


---

### Post by BicyclerBoy on 2010-12-17
I can not comment on your xorg.conf directly but

In your screen sections there should be 
Identifier    "Screen0"
Device       "Device0"
Monitor      "Monitor0"
   - replace the name-strings with yours to link the screen to device to monitor

In your device section there option keywords I don't recognize.
Option	    "Monitor-DFP1" "0-DFP1"
-   I don't think the link from device to monitor should be here.

Please note I'm no xorg expert.
I think multiple screens control is one of the biggest weakness in X server.

My observations with nvidia video cards is that there is a priority determined at boot up based on connection type & display capability.
This effects the POST output & sets terminal/stdout primary screen.
IMO the nvidia driver/firmware ranks hdmi > dvi > vga > other
It also ranks edid > non-edid

This observed 'rule' was broken by the nvidia GT240 which (for me) is ranking non-edid VGA > edid-dvi...

This all effects the X server choice of primary login screen for GUI. 
To fix this I swapped the screens in the xorg.conf.

So I have POST & startup script stdout on 'wrong' monitor.
And X server screen0 & GUI login on 'correct' monitor.

---

### Post by complience on 2010-12-18
Thanks for your input bikerboy, Im using a ATI card and Proprietary  drivers.

As your not an xorg expert, I don't think I should try your suggestions at alternating my xorg file.

The problem seems to be related to how amdcccle links ports to monitors.

I have two outputs (HDMI & DVI) whatever monitor is attached to the HDMI port is defaulted as the 'primary' monitor.

If i boot without anything attached to the HDMI, then the DVI is primary but if a monitor is attached to the HDMI the DVI output dynamicly changes to the secondary.

Is there anything in Xorg config that is doing this.. or is amdcccle working on its own?

---

### Post by BicyclerBoy on 2010-12-20
I had the same problem.
The xorg.conf file allows you to swap over which monitor is primary to the X server GUI.
I believe what I said before still stands.
The link from device to screen to monitor is wrong.

But I don't think your xorg.conf file arrangement is suitable for my fix.

The xorg.conf file is explained in the Xorg website & should be expalined in the video driver docs. The nvidia driver docs are very good & still applicable.

You are right to be cautious about editing this file..Just get comfortable editing it from terminal logout & no GUI..I did.

---

### Post by BicyclerBoy on 2010-12-20
This how I think it should be ..check xorg logs for errors..

You can swap Screen to Device binding ...

Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
# above confusing but not wrong
# Screen      0 1 0 0
# LeftOf ""  RightOf ""
 EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "false"
    Option        "PreferredMode" "1360x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
EndSection

Section "Monitor"
  Identifier   "0-DFP2"
  Option        "VendorName" "ATI Proprietary Driver" 
  Option        "ModelName" "Generic Autodetecting Monitor"
       Option        "DPMS" "true"
       Option        "PreferredMode" "1360x768"
       Option        "TargetRefresh" "60"
       Option        "Position" "0 0"
       Option        "Rotate" "normal"
       Option        "Disable" "false"
EndSection

Section "Device"
       Identifier  "Default Device"
       Driver      "fglrx"
   Screen 0
#       Option        "Monitor-DFP1" "0-DFP1"
 #      Option        "Monitor-DFP2" "0-DFP2"
  BusID       "PCI:1:0:0"
EndSection

Section "Device"
       Identifier  "amdcccle-Device[1]-0"
       Driver      "fglrx"
   Screen 1
#       Option        "Monitor-DFP2" "0-DFP2"
       BusID       "PCI:1:0:0"
EndSection

Section "Screen"
       Identifier "Default Screen"
       Device "Default Device"
   Monitor "0-DFP1"
   DefaultDepth     24
       SubSection "Display"
              Virtual   3280 1080
       EndSubSection
EndSection

Section "Screen"
       Identifier "amdcccle-Screen[1]-0"
       Device     "amdcccle-Device[1]-0"
   Monitor "0-DFP2"       
DefaultDepth     24
       SubSection "Display"
             Viewport   0 0
             Depth     24
       EndSubSection
EndSection

---

### Post by BicyclerBoy on 2010-12-20
You also need this inside the screen section for the attached monitor that does not report an EDID and/or does not auto detect connection.

    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"

Replace "CRT-0" with "DFP" or "DFP-1" as your 2 monitors should be seen as DFP-0 & DFP-1

---

### Post by complience on 2010-12-22
Thanks for looking closer bicycler

The problem is amdccle will edit/amend the xorg.conf file to its own liking.

I need two Screens because my monitors are not mirrored.
They are effectively two separate desktops although you can drags windows between them.

Your conf only seems to have one listed in the layout?
why should I #hash out the monitors from the device options?

Although its the same card would my HDMI output & DVI output have different BUSIDs?

I'm starting to think this is more of a xrandr problem and not a Xorg issue because the change happens dynamicly when the second screen is plugged in.

---

### Post by tjones00 on 2010-12-22
Working multi-display xorg.conf from a newly installed 32b 10.10 system with 2 x ATI radeon HD 4870 and 3 monitors using ATI proprietary driver provided by Ubuntu Additional Drivers. 1 display on the primary card 2 displays on the 2ndary card.

Hopefully studying the 2nd card config will clear up any xorg.conf issues for you.



```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 1024
    Screen         "aticonfig-Screen[1]-0" 1920 0
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "on"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 1024"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "1-DFP1"
    Option        "Monitor-DFP2" "1-DFP2"
    BusID       "PCI:6:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3200 3200
        Depth     24
    EndSubSection
EndSection

```I used aticonfig --adaptor=all --initial to generate the base xorg.conf and ATI Catalyst Control Center to configure the displays.

Maybe aticonfig --initial=dual-head will sort your issue out.

the contents of aticonfig --help


```
Usage: aticonfig [OPTION] ...
Parses an existing X-Server configuration file and modifies it to operate with
ATI products.

The following command-line options can be invoked as parameters:

ATI Initial Configuration:
  --initial
        Generate a default ATI device section in the configuration file which
        is capable of loading the fglrx driver.
  --initial=dual-head
        Same as '--initial' but generate a basic dual head configuration file.
  --initial=check
        Identifies if the fglrx driver is present in configuration file.

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
Screen-Related Options:
  --ovt, --overlay-type=STRING
        Change the overlay for the X server.  STRING can be one of:
            opengl
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
  --sm, --stereo-mode={active | passive | passiveInvertHorz | passiveInvertVert | horizontalInterleave | verticalInterleave | off}
        Enable/disable stereo support.  Enable active option only for
        applications that support the use of hardware 3D shutter glasses.
        For the use of passive, passiveInvertHorz, passiveInvertVert, horizontalInterleave and verticalInterleave modes
        specialized monitor equipment is required.
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
Advanced Options:
  --sync-video={on|off}
        Enable/disable sync to vsync for AVIVO video.
        This option is enabled by default and is used to prevent
        video tearing. By disabling this option video is free to
        render as fast as the 3D engine can handle. In the case of
        choppy video try to disable sync-video.
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
  --max-gart-size=VALUE1,VALUE2
        Set user-defined max total GART size(VALUE1) and cacheable gart
        size(VALUE2) for non-AGP systems.
        This option can combined with --adapter option to set the gart size
        for individual card. 

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
            cv
            tmds1
            tmds2
            tmds2i
            dfp3
            dfp4
            dfp5
            dfp6
            auto   -- use default policy to enable the displays.
  --query-monitor
        This will return connected and enabled monitor information
  --swap-monitor
        This only works for big desktop setup. This will swap the
        contents on the two monitors.
  --swap-screens={on|off}
        Enable/disable swap heads in dual-head mode.
        This option works only in dual-head mode.

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

Display attribute options:
  Following options are used for query and set adjustment of 
  specific attribute for specific display. These options will be 
  effective immediately. Other options on the same command line 
  will be ignored.
  The DISPLAYTYPE in options can be one of the following strings:
        crt1,  lvds,   tv,   cv,   tmds1, crt2,
        tmds2, tmds2i, dfp3, dfp4, dfp5,  dfp6 .
   The ATTRIBTYPE in options can be one of the following strings:
        brightness, contrast, saturation, hue, positionX, 
        positionY, sizeX, sizeY, overscan, videoStandard  
  --query-dispattrib=DISPLAYTYPE,ATTRIBTYPE 
        query the specific adjustment info of the specific display.
        if ATTRIBTYPE is not specified, all supported attribute 
        information will be printed out. 
  --set-dispattrib=DISPLAYTYPE,ATTRIBTYPE:VALUE 
        set the attribute value of the specific display.

Connector type options:
  Following options are used for query connector type 
  for specific display. These options will be 
  effective immediately. Other options on the same command line 
  will be ignored.
  The DISPLAYTYPE in options can be one of the following strings:
        crt1,  lvds,   tv,   cv,   tmds1, crt2,
        tmds2, tmds2i, dfp3, dfp4, dfp5,  dfp6 .
   --query-connectortype=DISPLAYTYPE 
        query the connector type of the specific display.

Component video dongle options:
  Following options are used for query and set dongles for a 
  component video. These options will be effective immediately.
  Other options on the same command line will be ignored.
  --query-cvdongle
        query dongle setting informations of the component video.
  --set-cvdongle=VALUE
        set the custom override value of the CV dongle. 
  --reset-cvdongle
        reset the custom override setting(to zero)of the CV dongle.

Component video customized mode options:
  Following options are used for query and set customized mode for
  component video. These options will be effective immediately.
  Other options on the same command line will be ignored.
  --query-cvmode
        query customized modes for component video.
  --add-cvmode=WIDTH,HEIGHT,FLAGS,BASEWIDTH,BASEDHEIGHT,REFRESH.
        add a customized mode for component video.
  --validate-cvmode=WIDTH,HEIGHT,FLAGS,BASEWIDTH,BASEHEIGHT,REFRESH.
        validate a customized mode for component video.
  --delete-cvmode=INDEX 
        delete one customized mode for component video. 

Persistent Configuration Store (PCS) Options:
  Following options will not change the config file. They are
  used to manipulate the PCS database.  Due to their nature, these.
  commands may only be run by the root user. Note that the prefix
  and key names are not case-sensitive.
  --get-pcs-key=PREFIX,KEY
        Prints out the specified prefix and key from the PCS
        database.  The type of data will be shown along with
        the contents.
  --set-pcs-u32=PREFIX,KEY,VALUE
  --set-pcs-val=PREFIX,KEY,VALUE (deprecated)
        Sets an integer value at the specified prefix and key in
        the PCS database.  The value may be specified in hex by
        prefixing it with 0x or in octal by prefixing it with 0,
        otherwise the value is assumed to be in decimal.  Note
        that --set-pcs-val is deprecated and --set-pcs-u32 should
        be used instead.  --set-pcs-val will be removed soon.
  --set-pcs-u32array=PREFIX,KEY,VALUE[,VALUE]...
        Sets an array of integer values at the specified prefix
        and key in the PCS database.  The values may be specified
        in hex by prefixing it with 0x or in octal by prefixing
        it with 0, otherwise the value is assumed to be in decimal.
        (e.g. --set-pcs-u32array="TestSection,TestData,1,0x2,3")
  --set-pcs-str=PREFIX,KEY,STRING
        Sets a string value at the specified prefix and key in
        the PCS database.
  --set-pcs-raw=PREFIX,KEY,HEXSTRING
        Sets a raw binary value at the specified prefix and key in
        the PCS database.  The value is specified as a series of
        hex bytes with no 0x or spaces.
        (e.g. --set-pcs-raw="TestSection,TestData,E84C0E" sets 3 bytes)
  --set-pcs-bool=PREFIX,KEY,VALUE
        Sets a boolean value at the specified prefix and key in
        the PCS database.  The value may be specified as either
        "true", "yes", "on", "enable" or "1" meaning boolean TRUE or
        "false", "no", "off", "disable" or "0" meaning boolean FALSE.
  --del-pcs-key=PREFIX,KEY
        Deletes the specified prefix and key from the PCS database.

Multiple display adapter options:
  Following options are used for querying and setting up multiple
  display adapters that are installed for multihead or Crossfire
  configurations.
  --lsa, --list-adapters
        Lists all detected and supported display adapters.
        The default adapter (used when --adapter is not specified)
        will be indicated with a "*" next to it.
  --adapter=ADAPTERLIST
        Selects which adapters returned by --list-adapters should
        be affected by other aticonfig options.  ADAPTERLIST contains
        either a comma-seperated sequence of the index numbers of the
        adapters to be affected or else contains the keyword "all" to
        select all the adapters.  If --adapter is missing, only the
        default adapter will be affected.
  --lscc, --list-crossfire-candidates
        Queries the driver to determine the pool of available devices that can
        can be chained together for CrossFire.
  --lscs, --list-crossfire-status
        List current Crossfire status (enabled or disabled) along with diagnostics
        information indicates the status of your system
  --lsch, --list-crossfire-chains
        Lists the CrossFire chains that are currently defined along with their
        enabled state
  --cfa, --add-crossfire-chain
        Defines a new CrossFire chain.  --adapter should contain the adapter
        chain definition, with the master adapter being the first entry and
        the slave adapters being the subsequent entries in order of priority.
  --cfd, --delete-crossfire-chain
        Delete and existing defined CrossFire chain.  --adapter should list the
        master adapters of the chains to be deleted.  --adapter=all will delete
        all chain definitions.
  --cf, --crossfire={on|off}
        Enables/disables CrossFire support on the currently defined CrossFire
        chains.  --adapter should list the master adapters to be enabled or
        disabled.
  --cfl, --crossfire-logo={on|off}
        Enables/disables the appearance of the CrossFire Logo when rendering
        in CrossFire mode

ATI Overdrive (TM) options:
  The following options are used to get and set current and peak, core
  and memory clock information as well as read the current temperature of
  adapters.  By using the "--adapter=" argument the ATI Overdrive (TM)
  options can be targeted to a particular adapter in a multi-adapter scenario.
  If no adapter is explicitly targeted the commands will be run on the Default
  adapter as indicated by the "--list-adapters" command
  --od-enable
        Unlocks the ability to change core or memory clock values by
        acknowledging that you have read and understood the ATI Overdrive (TM)
        disclaimer and accept responsibility for and recognize the potential
        dangers posed to your hardware by changing the default core or memory
        clocks
  --od-disable
        Disables ATI Overdrive(TM) set related aticonfig options.  Previously
        commited core and memory clock values will remain, but will not be set
        on X Server restart.
  --odgc, --od-getclocks
        Lists various information regarding current core and memory clock
        settings.
        Including: current and peak clocks
                   the theoretical range clocks can be set to
                   the current load on the GPU
  --odsc, --od-setclocks={NewCoreClock|0,NewMemoryClock|0}
        Sets the core and memory clock to the values specified in MHz
        The new clock values must be within the theoretical ranges provided
        by --od-getclocks.  If a 0 is passed as either the NewCoreClock or
        NewMemoryClock it will retain the previous value and not be changed.
        There is no guarantee that the attempted clock values will succeed
        even if they lay inside the theoretical range.  These newly set
        clock values will revert to the default values if they are not
        committed using the "--od-commitclocks" command before X is
        restarted
  --odrd, --od-restoredefaultclocks
        Sets the core and memory clock to the default values.
        Warning X needs to be restarted before these clock changes will take
        effect
  --odcc, --od-commitclocks
        Once the stability of a new set of custom clocks has been proven this
        command will ensure that the Adapter will attempt to run at these new
        values whenever X is restarted
  --odgt, --od-gettemperature
        Returns the temperature reported by any thermal sensors available on
        the adapter.

ACPI Options:
  --acpi-services=on|off
        Enable/disable ACPI services. In the case of BIOS or kernel ACPI issues,
        ACPI services in the driver can be disabled through this option.
        The ACPI services are enabled by default.
  --acpi-display-switch=on|off
        Enable/disable display switching with ACPI methods on mobile platforms.
        This option is enabled by default.

Genlock/Framelock options:
  The following options are used to control operation with GLSYNC module
  in the system.  By using the "--adapter=" argument --glsync-getconfig,
  --glsync-setconfig, --glsync-getgenlock, --glsync-setgenlock options
  can be targeted to a particular adapter in a multi-adapter scenario.
  If no adapter is explicitly targeted the commands will be run on the Default
  adapter as indicated by the "--list-adapters" command
  --glsync-getport={RJ45_1 | RJ45_2 | BNC}
        Get configuration state for specified GLSync port.
        Including: Number of LEDs
                   Scanned frequency
                   Signal Source for RJ45 port if it is configured as output 
                   Port state (Input or Output) for RJ45 port
                   Signal type for BNC port
  --glsync-setport=port_type,cntl,sig_src
        Set configuration for specified GLSync port
        Parameters: port_type - RJ45_1 or RJ45_2
                                only RJ45 ports can be configured
                    cntl - 0 if port is configured as input or
                           1 if port is configured as output
                    sig_src - signal source for GL Sync port
                              if 0-3 - GPU port index
                              if RJ45_1, RJ45_2 or BNC - another GL Sync port
                              if -1  - signal source is undefined
  --glsync-getconfig
        Get timing configuration for particular GL Sync connector
        Including: Sync Delay in ms
                   Signal Source
                   Sample Rate
                   Sync field
                   Trigger Edge
                   Scan Rate multiplier
                   GPU port index this adapter connected to
  --glsync-setconfig=delay,fr_cntl,sig_src,smpl_rate,fld,edge,coef
        Set timing configuration for GL Sync connector
        Parameters: delay - Sync Delay in ms
                    fr_cntl - Enable/Disable framlock control 
                              0 Disable Framelock
                              1 Enable Framelock
                    sig_src - Signal Source for this adapter.
                              if 0-3 - GPU port index.
                                   It can not be GPU port index of this adapter
                              if RJ45_1, RJ45_2 or BNC - GL Sync port
                              if -1  - signal source is undefined
                    smpl_rate - Sample Rate for sampled sync signal.
                              0 for no sampling
                    fld - Sync field for interlaced sync signal. 
                              0 if sync field is undefined
                              1 if synced to both field
                              2 if synced to field 1
                    edge - it is defined which signal edge
                                 should trigger syncronization
                              0 if edge is undefined
                              1 if it is triggered by raising edge
                              2 if it is triggered by falling edge
                              3 if it is triggered by both edges
                    coef - Scan Rate multiplier applied to sync signal
                              0 if coef is undefined
                              1 if coef is 5
                              2 if coef is 4
                              3 if coef is 3
                              4 if coef is 2.5
                              5 if coef is 2
                              6 if coef is 1.33
                              7 if coef is 1.25
                              8 if coef is 1.
                              9 if coef is 0.8
                             10 if coef is 0.67
                             11 if coef is 0,5
                             12 if coef is 0.4
                             13 if coef is 0.33
                             14 if coef is 0.25
                             15 if coef is 0.2
        Note: Some parameters may not be valid for manual configuration.
              Please use --glsync-getconfig command to verify.
  --glsync-getgenlock=disp_type
        Get genlock mode for particular display
        disp_type  - Display Type. When RandR 1.2 and above is enabled
                     can be query by using xrandr -q command.
                     If RandR 1.2 is not enabled
                     aticonfig --query-monitor command should be used
                     to query this parameter
  --glsync-setgenlock=disp_type,mode,timing_server
        Set genlock mode for particular display
        Parameters: disp_type  - Display Type.
                                 When RandR 1.2 and above is enabled
                                 can be query by using xrandr -q command.
                                 If RandR 1.2 is not enabled
                                 aticonfig --query-monitor command
                                 should be used to query this parameter.
                    mode       - Enable/Disable Genlock
                                 0 Disable Genlock
                                 1 Enable Genlock
                    timing_server - Enable/Disable timing server
                                 0 to configure display as free run
                                 1 to configure display as a timing server
  --glsync-restart
        Reinitialized all genlock settings after power down system

X Server Options:
  --xinerama={on|off}
        Enable/disable Xinerama (MultiView) in the X Server configuration file.
        MultiView allows for the merging of independent desktop heads into a
        unified workspace allowing windows to freely cross X Screen boundaries.

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

Composite options:
  --xv-pixmap-buffer-type=gartcacheable
       Allocate pixmap buffer from GART cacheable heap.
  --xv-pixmap-buffer-type=lfb
       Allocate pixmap buffer from local framebuffer.
  --xv-pixmap-buffer-type=gartuswc
       Allocate pixmap buffer from GART USWC heap.

Examples:
  1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
       Dual head   :    aticonfig --initial=dual-head --screen-layout=above
                        This command will generate a dual head configuration
                        file with the second screen located above the first
                        screen.
       Multi head  :    aticonfig --initial --heads=4 --adapter=1
                        This command will generate 4 adjacent X Screens
                        on adapter 1.  Use with -f to reduce previously configured heads.
  2. Setting up big desktop to horizontal and set overlay on secondary display.
                        aticonfig --dtop=horizontal --overlay-on=1
  3. Setting up modes for primary display.
                        aticonfig --resolution=0,1600x1200,1280x1024,1024x768
  4. Change tv geometry 
                         aticonfig --tv-geometry=85x90+10-10 
         This will set tv to 85% width (where 100% ==
         overscan) 90% height and shift 10 pixels right of centre
         and 10 pixels down of centre. 
  5. Multiple display adapters.
       List adapters :  aticonfig --list-adapters
       Init 0 and 2  :  aticonfig --adapter=0,2 --initial
       Init all      :  aticonfig --adapter=all --initial
       MultiView     :  aticonfig --xinerama=on
  6. ATI Overdrive (TM).
       List adapters          :  aticonfig --list-adapters
       Get Clocks of 0        :  aticonfig --adapter=0 --od-getclocks
       Set new Clocks for 0   :  aticonfig --adapter=0 --od-setclocks=770,1126
       Test out 3D            :  atiode -P60 -H localhost:0; echo $?
       Check Temperature of 0 :  aticonfig --adapter=0 --od-gettemperature
       Commit changes for 0   :  aticonfig --adapter=0 --od-commitclocks

     ***note***
             atiode is a stress application you start with a required
             parameter -P which specifies the test duration and the optional
             -H parameter to target a specific display to use.  For example
             atiode -P 600 -H localhost:0 would test display 0 for 10 minutes
             the return code from the application is the test result
             0: Test successfully completed.
             1: Invalid command-line parameters.
             2: Test failed because of rendering errors.
             3: Target adapter not found.
             4: Test aborted due to unknown reason

  7. Framelock/Genlock with GL Sync module
       Set GL Sync connector parameters for particular adapter: 
                     aticonfig --glsync-setconfig=0,0,2,0.0,3,8 --adapter=1
       Enable Genlock for particular display:
                     aticonfig --glsync-setgenlock=lvds,1,0 --adapter=1
       Enable Timing Master:
                     aticonfig --glsync-setgenlock=dfp3,0,1 --adapter=1
       Verify if the frequiency is locked for particular display:
                     aticonfig --glsync-getgenlock=crt1 --adapter=1
       Set GL Sync output port RJ45_1:
                     aticonfig --glsync-setport=RJ45_1,1,BNC
       Reinitialize all genlock settings for all displays and adapters:
                     aticonfig --glsync-restart

Please report bugs to http://support.ati.com
```

---

### Post by complience on 2010-12-22
To be honest now im just more confused than ever..

I'm now outputting the DFP1 monitor to the DVI output
It shows the correct panel and desktop items of screen 1.

But now there is no mouse or keyboard response, where have they gone?

Below is my current xorg.conf


[PHP]
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
	Screen      1  "amdcccle-Screen[2]-0"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1360x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1360x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	screen 1
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	screen 0
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-0"
	Device     "amdcccle-Device[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   2720 768
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   2720 1920
		Depth     24
	EndSubSection
EndSection
[/PHP]

---

### Post by complience on 2010-12-22
think its related to the busid ive given in 'devices' 
removed it and got the mouse back.. but the old problem returns - when you plug in the second monitor the screen just shows the background image and nothing else..

starting to think ubuntu just can't do this with this card.

just found this! this could be it!

[https://wiki.archlinux.org/index.php/ATI#Independent_X_Screens](https://wiki.archlinux.org/index.php/ATI#Independent_X_Screens)

---

### Post by complience on 2010-12-23
The "ZaphodHeads" option may solve the original problem, but now I have the new problem of no mouse when I enter a busid for the graphics card in the devices section.

I do seem to have a keyboard because an ctrl, alt, F1 changes the screen.
However the TTY does not appear the screen just goes black, a ctrl, alt, f7 brings the desktop backup (still with no mouse)

---

### Post by BicyclerBoy on 2010-12-28
Using *buntu 10.04 nvidia 260 drivers..manually edited xorg.conf after driver install.
One videocard twinhead configured as separate x screens
No xinerama
No twinview
So not mirrored/cloned, menus on both screens, apps run full screen independently, mouse moves between screens, NO icons possible on 2nd screen so far, full hardware accelerated HD video on any screen.

Have noticed that the BUSID keyword is not used/required any more.

The AMD/ATI config tool is similar to nvidia-settings IFAIK.
The nvidia settings/config tool makes a mess of the xorg.conf file but it allows you to merge & review/edit any changes.

My xorg.conf has still has entries for keyboard & mouse.

[PHP]
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:36:15 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option       "Xinerama" "0"
EndSection

Section "ServerLayout"
    Identifier     "Layout1"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option       "Xinerama" "0"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
    Option         "DefaultServerLayout" "Layout0"
#    Option         "TwinViewXineramaInfoOrder" "CRT-1 , CRT-0"
#    Option         "UseEvents" "True"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Modes"
#    Modeline       "1920x1080i60" 77.6  1920 1980 2268 2272 1080 1104 1110 1135 +HSync +VSync Interlace
# more sync time hs 4us vs 200us
#       Modeline       "1920x1080i60" 78.21 1920 1972 2284 2304 1080 1104 1111 1135 +HSync +VSync interlace

    Identifier         "myHDTV"
#    ModeLine     "1920x1080i60" 79.0 1920 1984 2276 2320 1080 1104 1111 1135 +hsync +vsync interlace

#    Modeline     "2048x1152i50" 81.14  2048 2100 2660 2672 1152 1154 1168 1211 +hsync +vsync interlace
##    Modeline     "2048x1152i50"  72.75 2048 2080 2368 2400 1152 1176 1187 1211 +hsync +vsync interlace
    ModeLine     "1920x1080i60" 88.7   1920 2208 2252 2600 1080 1092 1100 1135 +hsync +vsync interlace
    Modeline     "1920x1080i50" 70.25 1920 1952 2440 2472 1080 1101 1113 1135  +hsync +vsync interlace
    ModeLine     "1280x720p60"  73.78  1280 1312 1592 1624  720  735  742  757 +hsync +vsync
    ModeLine     "1024x576p50"  37.19  1024 1056 1192 1224  576  588  593  605 +hsync +vsync
    ModeLine     "848x480p60"   31.23   848  880  992 1024  480  490  495  505 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP w19b/w19e"
    HorizSync       30.0 - 83.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Philips"
    ModelName      "32PW8808"
    UseModes       "myHDTV"
    HorizSync       22.0 - 47.0
    VertRefresh     48.0 - 65.0
#    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor11"
    VendorName     "Unknown"
    ModelName      "Samsung 210T Digital"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 240"
    Screen         0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 240"
    Screen         1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "UseDisplayDevice" "DFP-0"
    Option         "TwinView" "0"
#    Option         "metamodes" "DFP: 1600x1200 +0+0"  # here for samsung 210
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
#    Option         "XineramaPrimaryScreen" "1"
    Option         "ModeValidation" "AllowInterlacedModes"
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"
# should use custom Modes
#    Option         "metamodes" "CRT:1920x1080i60 +0+0; CRT:2048x1152i50 +0+0; CRT:1280x720p60 +0+0; CRT:1024x576p50 +0+0; CRT:848x480p60 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080i60" "2048x1152i50" "1280x720p60" "1024x576p50" "848x480p60"
#        Option     "PreferredMode" "1920x1080i60"
    EndSubSection
EndSection

Section "Extensions"
# nothing to do with video
#    Option         "Composite" "Disable"
EndSection

[/PHP]

But AMD/ATI could do things differently.

---

### Post by complience on 2010-12-29
Now when I turn on the second monitor the output on the first monitor still changes.

I can see the background desktop and a mouse cursor
(no icons or panel)

If i go to the TTY and run a xrandr -q
I get the following message back.

xrandr can not open display

---

### Post by complience on 2010-12-30
Apparently Xrandr doesn't support multiscreen..

crud

[http://davelargo.blogspot.com/2010/01/xrandr-no-more-xinerama.html](http://davelargo.blogspot.com/2010/01/xrandr-no-more-xinerama.html)

---

### Post by gewone on 2011-10-13
Wow. This thread (if any) describes my issue at the very pinpoint. I nee my television set and my desk VGA monitor switched. The telly always comes up as primary screen, with 'Buntu login and everything, and xorg.conf doesn't seem to apply (much) since ATI/CCC is installed. Thus I'ved tried "aticonfig --initial", yet nothing happens. Also the "--initial=dual-heads" fails to do me mercy. It _always_ gets to be the telly that's primary. Why can't ATI add a simple "Use as primary monitor" option to CCC? It's been there in the Windoze version for years, haven't it?

---

