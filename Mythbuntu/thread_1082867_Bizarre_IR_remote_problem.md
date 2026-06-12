---
title: "Bizarre IR remote problem"
date: 2009-02-28
forum: Mythbuntu
---

### Post by rduske on 2009-02-28
I am an experience Linux user new to Myth TV. I have read the forums and been consulting Dr. Google to help me with my IR remote problem for several days now to no avail.  I have even tried posting to the MythTV forums and developer mailinglists with no response.

I am running Mythbuntu 8.10 on a Dell XPS Gen2 laptop with a Pinnacle HD Pro Stick (801e) USB tuner. I was able to get most everything setup and working without too much difficulty.

My one problem is the IR remote. I am using a Logitech Harmony 880 setup as a Hauppauge HVR-1100.

LIRC seems to be setup correctly, The MythTV frontend responds to the remote and allows me to navigate the interface. irw reports all the buttons correctly. When I go into Live TV however, the remote doesn't respond. Here's where it gets a little strange. When I enter LiveTV and press the Pause button on the remote nothing happens. I use Ctrl-Alt-F4 to switch to a terminal, log in and run irw. when I press the Pause button, I get the irw line that indicates that it detected the Pause button press. I also hear the audio from the LiveTV stop. When I switch back to the LiveTV window, I see that the video is paused! The LiveTV window is responding to the remote, but only when switched to a different terminal. I obviously have something configured incorrectly, but I have been unable to determine exactly what. It seems like it might be a focus problem, but I have tried configuring the window manager to follow the mouse for focus, that did not help.

Any assistance you can give me would be greatly appreciated.

-- Rick Duske

---

### Post by azmyth on 2009-02-28
First of all, make sure lirc is enabled even though I'm sure it is but always like to check

mythbackend --version

You should see enabled-lirc

Make sure you have the .lircrc file in the following /home/username directory. I put the file in one and link to the other so you don't have to change both.

.lircrc 
/.mythtv/lircrc

Close the frontend and open a terminal and start mythfrontend from there. If lirc can't connect, you'll see an error message.

---

### Post by rduske on 2009-02-28
Thanks for getting back to me.  

Yes, lirc is enabled on the front-end.  Plus, I have .lircrc setup, in the home directory and  linked into ~/.mythtv/lircrc

I tried your suggestion about starting the MythTV in a terminal and looking at the errors.  I see some interesting messages about "prebuffering pause", but nothing obvious.  I have attached the output, and the copy of my .lircrc file.

-- Rick

---

### Post by rduske on 2009-02-28
Hmmm....attachments didn't upload.  Here's the output from the terminal window:
> 
rduske@fozzie:~$ mythbackend --version
Please include all output in bug reports.
MythTV Version   : 18722
MythTV Branch    : branches/release-0-21-fixes
Library API      : 0.21.20080304-1
Network Protocol : 40
Options compiled in:
 linux profile using_oss using_alsa using_arts using_jack using_backend using_dbox2 using_dvb using_firewire us
ing_frontend using_hdhomerun using_iptv using_ivtv using_joystick_menu using_libfftw3 using_lirc using_opengl_v
sync using_opengl_video using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmcw using_xvmc_vld using_g
lx_proc_addr_arb using_bindings_perl using_bindings_python using_opengl using_ffmpeg_threads using_libavc_5_3 u
sing_live
rduske@fozzie:~$ ls -la .lircrc
-rw-r--r-- 1 rduske rduske 296 2009-02-18 23:12 .lircrc
rduske@fozzie:~$ ls -la .mythtv/lircrc
lrwxrwxrwx 1 rduske rduske 10 2009-02-20 22:58 .mythtv/lircrc -> ../.lircrc
rduske@fozzie:~$ mythfrontend
2009-02-28 16:20:54.231 Using runtime prefix = /usr
2009-02-28 16:20:54.833 XScreenSaver support enabled
2009-02-28 16:20:54.833 DPMS is active.
2009-02-28 16:20:54.833 Empty LocalHostName.
2009-02-28 16:20:54.833 Using localhost value of fozzie
2009-02-28 16:20:54.839 New DB connection, total: 1
2009-02-28 16:20:54.859 Connected to database 'mythconverg' at host: localhost
2009-02-28 16:20:54.861 Closing DB connection named 'DBManager0'
2009-02-28 16:20:54.877 Primary screen 0.
2009-02-28 16:20:54.878 Connected to database 'mythconverg' at host: localhost
2009-02-28 16:20:54.879 Using screen 0, 1920x1200 at 0,0
2009-02-28 16:20:54.914 New DB connection, total: 2
2009-02-28 16:20:54.916 Connected to database 'mythconverg' at host: localhost
2009-02-28 16:20:54.918 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-02-28 16:20:54.918 Enabled verbose msgs:  important general
2009-02-28 16:20:55.515 No theme dir: /home/rduske/.mythtv/themes/Mythbuntu-8.04-wide
2009-02-28 16:20:55.520 Primary screen 0.
2009-02-28 16:20:55.521 Using screen 0, 1920x1200 at 0,0
2009-02-28 16:20:55.521 No theme dir: /home/rduske/.mythtv/themes/Mythbuntu-8.04-wide
2009-02-28 16:20:55.521 Switching to wide mode (Mythbuntu-8.04-wide)
2009-02-28 16:20:55.539 Using the OpenGL painter
2009-02-28 16:20:55.543 lirc init success using configuration file: /home/rduske/.mythtv/lircrc
2009-02-28 16:20:55.556 JoystickMenuClient Error: Joystick disabled - Failed to read /home/rduske/.mythtv/joyst
ickmenurc
2009-02-28 16:20:56.700 Specified base font 'medium' does not exist for font clock
2009-02-28 16:20:56.700 Specified base font 'medium' does not exist for font small
2009-02-28 16:20:56.700 Specified base font 'medium' does not exist for font medium
2009-02-28 16:20:56.700 Specified base font 'medium' does not exist for font large
2009-02-28 16:20:56.702 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2009-02-28 16:20:56.759 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-02-28 16:20:56.793 Registering Internal as a media playback plugin.
2009-02-28 16:20:56.861 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-02-28 16:20:56.890 Failed to run 'cdrecord --scanbus'
2009-02-28 16:20:56.902 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-02-28 16:20:56.904 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-02-28 16:20:56.921 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.124.13:5060 NAT address 192.168.124.13
SIP: Cannot register; proxy, username or password not set
2009-02-28 16:20:56.998 No theme dir: /home/rduske/.mythtv/themes/Mythbuntu-8.04-wide
2009-02-28 16:20:58.038 Using NV NPOT texture extension
2009-02-28 16:22:59.173 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-28 16:22:59.173 Using protocol version 40
2009-02-28 16:22:59.185 TV: Attempting to change from None to WatchingLiveTV
2009-02-28 16:22:59.188 Using protocol version 40
2009-02-28 16:23:00.326 DPMS Deactivated 
2009-02-28 16:23:00.379 New DB connection, total: 3
2009-02-28 16:23:00.380 Connected to database 'mythconverg' at host: localhost
2009-02-28 16:23:00.405 NVP: Disabling Audio, params(-1,2,44100)
2009-02-28 16:23:00.478 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-02-28 16:23:00.551 OSD Theme Dimensions W: 640 H: 480
2009-02-28 16:23:01.140 TV: Changing from None to WatchingLiveTV
2009-02-28 16:23:01.144 Realtime priority would require SUID as root.
2009-02-28 16:23:01.246 OpenGLVideoSync()
2009-02-28 16:23:01.295 Video timing method: SGI OpenGL
2009-02-28 16:23:02.853 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-02-28 16:23:03.500 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-02-28 16:23:03.500 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-02-28 16:23:03.505 AFD: Opened codec 0x8e83000, id(MPEG2VIDEO_XVMC) type(Video)
2009-02-28 16:23:03.505 AFD: codec AC3 has 6 channels
2009-02-28 16:23:03.573 AFD: Opened codec 0x8eb6610, id(AC3) type(Audio)
2009-02-28 16:23:03.674 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-02-28 16:23:03.674 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-02-28 16:23:03.850 Opening audio device 'default'. ch 2(2) sr 48000
2009-02-28 16:23:03.850 Opening ALSA audio device 'default'.
2009-02-28 16:23:03.856 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-02-28 16:23:03.856 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-02-28 16:23:03.930 NVP: Enabling Audio
2009-02-28 16:23:03.976 XvMC: picture structure FRAME
2009-02-28 16:23:07.291 WriteAudio: buffer underrun
2009-02-28 16:23:07.366 WriteAudio: buffer underrun
2009-02-28 16:23:07.469 WriteAudio: buffer underrun
2009-02-28 16:23:07.586 WriteAudio: buffer underrun
2009-02-28 16:23:07.703 WriteAudio: buffer underrun
2009-02-28 16:23:07.812 WriteAudio: buffer underrun
2009-02-28 16:23:07.881 WriteAudio: buffer underrun
2009-02-28 16:23:07.942 WriteAudio: buffer underrun
2009-02-28 16:23:08.008 WriteAudio: buffer underrun
2009-02-28 16:23:08.049 WriteAudio: buffer underrun
2009-02-28 16:23:08.138 WriteAudio: buffer underrun
2009-02-28 16:23:08.268 WriteAudio: buffer underrun
2009-02-28 16:23:08.369 WriteAudio: buffer underrun
2009-02-28 16:23:08.477 WriteAudio: buffer underrun
2009-02-28 16:23:08.532 WriteAudio: buffer underrun
2009-02-28 16:23:08.600 WriteAudio: buffer underrun
2009-02-28 16:23:08.697 WriteAudio: buffer underrun
2009-02-28 16:23:08.704 NVP: prebuffering pause
2009-02-28 16:23:08.791 NVP: prebuffering pause
2009-02-28 16:23:16.387 NVP: prebuffering pause
2009-02-28 16:23:19.794 NVP: prebuffering pause
2009-02-28 16:23:20.103 NVP: prebuffering pause
2009-02-28 16:23:24.453 NVP: prebuffering pause
2009-02-28 16:23:24.870 NVP: prebuffering pause
2009-02-28 16:23:35.108 NVP: prebuffering pause
2009-02-28 16:23:35.154 NVP: prebuffering pause
2009-02-28 16:23:35.203 NVP: prebuffering pause
2009-02-28 16:23:35.255 NVP: prebuffering pause
2009-02-28 16:23:35.288 NVP: prebuffering pause
2009-02-28 16:23:35.361 NVP: prebuffering pause
2009-02-28 16:23:35.418 NVP: prebuffering pause
2009-02-28 16:23:35.468 NVP: prebuffering pause
2009-02-28 16:23:35.511 NVP: prebuffering pause
2009-02-28 16:23:35.550 NVP: prebuffering pause
2009-02-28 16:23:35.602 NVP: prebuffering pause
2009-02-28 16:23:36.662 NVP: prebuffering pause
2009-02-28 16:23:36.730 WriteAudio: buffer underrun
2009-02-28 16:23:40.283 NVP: Prebuffer wait timed out 10 times.
2009-02-28 16:23:40.543 AFD: Opened codec 0x8f43ad0, id(MPEG2VIDEO_XVMC) type(Video)
2009-02-28 16:23:40.543 AFD: codec AC3 has 6 channels
2009-02-28 16:23:40.544 AFD: Opened codec 0x9dd2550, id(AC3) type(Audio)
2009-02-28 16:23:43.242 WriteAudio: buffer underrun
2009-02-28 16:23:43.442 AFD: Opened codec 0x8f43ad0, id(MPEG2VIDEO_XVMC) type(Video)
2009-02-28 16:23:43.442 AFD: codec AC3 has 6 channels
2009-02-28 16:23:43.444 AFD: Opened codec 0x8f4b430, id(AC3) type(Audio)
2009-02-28 16:23:43.458 WriteAudio: buffer underrun
2009-02-28 16:23:43.669 VideoOutputXv: ProcessFrameXvMC:
			Warning, B is still marked as the OSD frame of A.
2009-02-28 16:23:44.172 WriteAudio: buffer underrun
2009-02-28 16:23:44.287 WriteAudio: buffer underrun
2009-02-28 16:23:44.360 WriteAudio: buffer underrun
2009-02-28 16:23:44.409 WriteAudio: buffer underrun
2009-02-28 16:23:44.569 NVP: prebuffering pause
2009-02-28 16:23:44.661 NVP: prebuffering pause
2009-02-28 16:23:44.703 NVP: prebuffering pause
2009-02-28 16:23:44.909 NVP: prebuffering pause
2009-02-28 16:23:51.314 TV: Attempting to change from WatchingLiveTV to None
2009-02-28 16:23:51.374 ~OpenGLVideoSync() -- begin
2009-02-28 16:23:51.374 ~OpenGLVideoSync() -- middle
2009-02-28 16:23:51.375 ~OpenGLVideoSync() -- end
2009-02-28 16:23:51.638 TV: Changing from WatchingLiveTV to None
2009-02-28 16:23:51.716 DPMS Reactivated.
Destroying SipFsm object 
2009-02-28 16:23:56.497 Deleting UPnP client...


Now, here's the lircrc (~/.lirc/mythtv)

> 
# ~/.mythtv/lircrc
#
# MythTV native LIRC config file for
# the new grey Hauppauge remote
#
# Modified from Jarod Wilson's which came from Jeff Campbell's
# By Brad Templeton


# Here we have the jump point commands.  They only work if you have
# defined function keys for these jump points.  For me the most
# common command is the menu of recordings, so I put that on "videos"
# even though that's counter-intuitive

begin
prog = mythtv
button = Tv
repeat = 0
config = F5
end

begin
prog = mythtv
button = Videos
repeat = 0
config = F2
end

# Not yet defined
begin
prog = mythtv
button = Music
repeat = 0
config = Up
end

# Given another function for now, I don't use mythgallery
begin
prog = mythtv
button = Pictures
repeat = 0
config = F
end

begin
prog = mythtv
button = Guide
repeat = 0
config = F3
end

# I stuck the "todo" list on here as Myth has no radio function
begin
prog = mythtv
button = Radio
repeat = 0
config = F4
end

begin
prog = mythtv
button = Up
repeat = 0
config = Up
end

begin
prog = mythtv
button = Down
repeat = 0
config = Down
end

begin
prog = mythtv
button = Left
repeat = 0
config = Left
end

begin
prog = mythtv
button = Right
repeat = 0
config = Right
end

# Channel Up
begin
prog = mythtv
button = Chan+
repeat = 0
config = Up
end

# Channel Down
begin
prog = mythtv
button = Chan-
repeat = 0
config = Down
end

# OK/Select
begin
prog = mythtv
button = Ok
config = Space
end

# Play
begin
prog = mythtv
button = Play
config = Return
end

# Stop
begin
prog = mythtv
button = Stop
config = I
end

# Escape/Exit/Back
begin
prog = mythtv
button = Exit
config = Esc
end

# Power Off/Exit
begin
prog = mythtv
button = Power
config = Esc
end


# Pause
begin
prog = mythtv
button = Pause
repeat = 0
config = P
end

# Mute
begin
prog = mythtv
button = Mute
repeat = 0
config = |
end

# Fast forward (30 sec default)
begin
prog = mythtv
button = Rew
repeat = 0
config = <
end

# Rewind (10 sec default)
begin
prog = mythtv
button = Fwd
repeat = 0
config = >
end

# Skip forward (10 min default)
begin
prog = mythtv
button = Fwd
repeat = 0
config = End
end

# Skip backward (10 min default)
begin
prog = mythtv
button = Rew
repeat = 0
config = Home
end

# Record
begin
prog = mythtv
button = Record
repeat = 0
config = R
end

# Delete
begin
prog = mythtv
button = red
repeat = 0
config = D
end

# Decrease play speed
begin
prog = mythtv
button = green
repeat = 0
config = J
end

# Display EPG while in live TV,
# View selected show while in EPG
begin
prog = mythtv
button = Menu
repeat = 0
config = M
end

# Scroll up
begin
prog = mythtv
button = Vol+
repeat = 0
config = F11
end

# Scroll down
begin
prog = mythtv
button = Vol-
repeat = 0
config = F10
end

# Bring up OSD info
begin
prog = mythtv
button = Go
repeat = 0
config = I
end

# Change display aspect ratio
begin
prog = mythtv
button = Prev-Channel
repeat = 0
config = W
end

# double speed watch
begin
prog = mythtv
button = yellow
repeat = 0
config = J
end

# change tuners
#begin
#prog = mythtv
#button = #
#repeat = 0
#config = Y
#end

# + (clear)
begin
prog = mythtv
button = *
repeat = 0
config = Esc
end

# E (Enter)
begin
prog = mythtv
button = #
repeat = 0
config = Space
end

# Bring up Time stretch
begin
prog = mythtv
button = blue
repeat = 0
config = A
end

# Numbers 0-9

begin
prog = mythtv
button = 0
repeat = 0
config = 0
end

begin
prog = mythtv
button = 1
repeat = 0
config = 1
end

begin
prog = mythtv
button = 2
repeat = 0
config = 2
end

begin
prog = mythtv
button = 3
repeat = 0
config = 3
end

begin
prog = mythtv
button = 4
repeat = 0
config = 4
end

begin
prog = mythtv
button = 5
repeat = 0
config = 5
end

begin
prog = mythtv
button = 6
repeat = 0
config = 6
end

begin
prog = mythtv
button = 7
repeat = 0
config = 7
end

begin
prog = mythtv
button = 8
repeat = 0
config = 8
end

begin
prog = mythtv
button = 9
repeat = 0
config = 9
end

#----------------------#
# Rhythmbox lirc setup
#----------------------#

begin
   prog = Rhythmbox
   button = play
   config = play
end
begin
   prog = Rhythmbox
   button = Pause
   config = pause
end
begin
   prog = Rhythmbox
   button = Stop
   config = stop
end
begin
   prog = Rhythmbox
   button = PrevChan
   config = shuffle
end

begin
   prog = Rhythmbox
   button = Previous
   config = previous
end

begin
   prog = Rhythmbox
   button = Next
   config = next
end
begin
   prog = Rhythmbox
   button = Mute
   config = mute
end
begin
   prog = Rhythmbox
   button = Vol+
   config = volume_up
end
begin
   prog = Rhythmbox
   button = Vol-
   config = volume_down
end
begin
   prog = Rhythmbox
   button = SKip
   config = seek_forward
end
begin
   prog = Rhythmbox
   button = replay
   config = seek_backward
end

#----------------------#
# Kaffeine lirc setup
#----------------------#

begin
        prog = irexec
        button = play
        config = dcop kaffeine KaffeineIface playDvb
end
begin
        prog = irexec
        button = Pause
        config = dcop kaffeine KaffeineIface pause
end
begin
        prog = irexec
        button = Ok
        config = dcop kaffeine KaffeineIface dvbOSD
end
begin
        prog = irexec
        button = Stop
        config = dcop kaffeine KaffeineIface stop
end
begin
        prog = irexec
        button = SKip
        config = dcop kaffeine KaffeineIface posPlus
end
begin
        prog = irexec
        button = replay
        config = dcop kaffeine KaffeineIface posMinus
end
begin
        prog = irexec
        button = Chan+
        config = dcop kaffeine KaffeineIface next
end
begin
        prog = irexec
        button = Chan-
        config = dcop kaffeine KaffeineIface previous
end
begin
        prog = irexec
        button = power
        config = dcop kaffeine KaffeineIface quit
end
begin
        prog = irexec
        button = Vol+
        config = dcop kaffeine KaffeineIface volUp
end
begin
        prog = irexec
        button = Mute
        config = dcop kaffeine KaffeineIface mute
end
begin
        prog = irexec
        button = Vol-
        config = dcop kaffeine KaffeineIface volDown
end
begin
        prog = irexec
        button = Go
        config = dcop kaffeine KaffeineIface fullscreen
end
begin
        prog = irexec
        button = Up
        config = dcop kaffeine KaffeineIface dvbOSDNextChannel
end
begin
        prog = irexec
        button = Down
        config = dcop kaffeine KaffeineIface dvbOSDPreviousChannel
end
begin
        prog = irexec
        button = Left
        config = dcop kaffeine KaffeineIface dvbOSDNextProgram
end
begin
        prog = irexec
        button = Right
        config = dcop kaffeine KaffeineIface dvbOSDPreviousProgram
end
begin
        prog = irexec
        button = 1
        config = dcop kaffeine KaffeineIface setNumber 1
   repeat = 0
end
begin
        prog = irexec
        button = 2
        config = dcop kaffeine KaffeineIface setNumber 2
   repeat = 0
end
begin
        prog = irexec
        button = 3
        config = dcop kaffeine KaffeineIface setNumber 3
   repeat = 0
end
begin
        prog = irexec
        button = 4
        config = dcop kaffeine KaffeineIface setNumber 4
   repeat = 0
end
begin
        prog = irexec
        button = 5
        config = dcop kaffeine KaffeineIface setNumber 5
   repeat = 0
end
begin
        prog = irexec
        button = 6
        config = dcop kaffeine KaffeineIface setNumber 6
   repeat = 0
end
begin
        prog = irexec
        button = 7
        config = dcop kaffeine KaffeineIface setNumber 7
   repeat = 0
end
begin
        prog = irexec
        button = 8
        config = dcop kaffeine KaffeineIface setNumber 8
   repeat = 0
end
begin
        prog = irexec
        button = 9
        config = dcop kaffeine KaffeineIface setNumber 9
   repeat = 0
end
begin
        prog = irexec
        button = 0
        config = dcop kaffeine KaffeineIface setNumber 0
   repeat = 0
end

#----------------------#
# Totem lirc setup
#----------------------#

begin
        prog = Totem
        button = play
        config = play
end
begin
        prog = Totem
        button = Pause
        config = pause
end
begin
        prog = Totem
        button = Next
        config = next
end
begin
        prog = Totem
        button = Previous
        config = previous
end
begin
        prog = Totem
        button = play
        config = play
end
begin
        prog = Totem
        button = SKip
        config = seek_forward
end
begin
        prog = Totem
        button = replay
        config = seek_backward
end
begin
        prog = Totem
        button = Vol+
        config = volume_up
end
begin
        prog = Totem
        button = Vol-
        config = volume_down
end
begin
        prog = Totem
        button = Go
        config = fullscreen
end
begin
        prog = Totem
        button = power
        config = quit
end
begin
        prog = Totem
        button = Up
        config = up
end
begin
        prog = Totem
        button = Down
        config = down
end
begin
        prog = Totem
        button = Left
        config = left
end
begin
        prog = Totem
        button = Right
        config = right
end
begin
        prog = Totem
        button = Ok
        config = select
end
begin
        prog = Totem
        button = Menu
        config = menu
end
begin
        prog = Totem
        button = Mute
        config = mute
end

#----------------------#
# Tvtime lirc setup
#----------------------#

begin
    prog = irexec
    button = Menu
    config = tvtime-command TOGGLE_INPUT
end
begin
    prog = irexec
    button = power
    config = tvtime-command QUIT
end
begin
    prog = irexec
    button = Go
    config = tvtime-command TOGGLE_FULLSCREEN
end
begin
    prog = irexec
    button = Mute
    config = tvtime-command TOGGLE_MUTE
end
begin
    prog = irexec
    button = Chan+
    config = tvtime-command UP
    repeat = 1
end
begin
    prog = irexec
    button = Chan-
    config = tvtime-command DOWN
    repeat = 1
end
begin
    prog = irexec
    button = Vol+
    config = tvtime-command RIGHT
    repeat = 2
end
begin
    prog = irexec
    button = Vol-
    config = tvtime-command LEFT
    repeat = 2
end
begin
    prog   = irexec
    button = 1
    config = tvtime-command CHANNEL_1
end
begin
    prog   = irexec
    button = 2
    config = tvtime-command CHANNEL_2
end
begin
    prog   = irexec
    button = 3
    config = tvtime-command CHANNEL_3
end
begin
    prog   = irexec
    button = 4
    config = tvtime-command CHANNEL_4
end
begin
    prog   = irexec
    button = 5
    config = tvtime-command CHANNEL_5
end
begin
    prog   = irexec
    button = 6
    config = tvtime-command CHANNEL_6
end
begin
    prog   = irexec
    button = 7
    config = tvtime-command CHANNEL_7
end
begin
    prog   = irexec
    button = 8
    config = tvtime-command CHANNEL_8
end
begin
    prog   = irexec
    button = 9
    config = tvtime-command CHANNEL_9
end
begin
    prog   = irexec
    button = 0
    config = tvtime-command CHANNEL_0
end
begin
    prog = irexec
    button = Ok
    config = tvtime-command ENTER
end 


The real puzzle is why irw reports the remote control's button presses only when task-switched to the alternate terminal window and why the LiveTV window only responds to the remote control at that time.

-- Rick

---

### Post by azmyth on 2009-02-28
please post your /etc/lirc/hardware.conf file.

Also the results from

ps -u root | grep lirc
ls -al /dev | grep lirc

---

### Post by rduske on 2009-03-01
I appreciate the help, but the mystery has been solved.  There was a bug in the hardware abstraction layer.  I downloaded and installed the correct lirc.fdi file and the problem was fixed.

Here's a link to the report I found that described the problem and resolution:

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627)

Once again, thanks!

-- Rick

---

