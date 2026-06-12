---
title: "Master Backend Connect Fails when Add Capture Card"
date: 2011-10-18
forum: Mythbuntu
---

### Post by linux.rog on 2011-10-18
When I attempt to add a video capture card, MythBuntu throws an error: Could not connect to master backend server. It's not a matter of wrong i.p. address, etc. Only happens when I choose a capture card.

My front and backend are on the same machine. I'm installing / running Mythbuntu 11.10 with a Hauppauge 1600 model 1199. It's quite new and the kernel (3.0.0-12) is said to support the 1600.The system seems to recognize the capture card and installs drivers.

There is not a listing for this capture card on the add-menu so I chose one that has MPEG-2 as part of its title.

I have not connected to a cable yet - just trying to get the software installed and hdw setup. 

I assume that the lack of response for my remote control is related to this.

Where do I go from here?

/Roger

---

### Post by thatguruguy on 2011-10-19
Have you considered trying it with the cable hooked up?

---

### Post by nickrout on 2011-10-19
> **linux.rog said:**
> When I attempt to add a video capture card, MythBuntu throws an error: Could not connect to master backend server. It's not a matter of wrong i.p. address, etc. Only happens when I choose a capture card.

My front and backend are on the same machine. I'm installing / running Mythbuntu 11.10 with a Hauppauge 1600 model 1199. It's quite new and the kernel (3.0.0-12) is said to support the 1600.The system seems to recognize the capture card and installs drivers.

There is not a listing for this capture card on the add-menu so I chose one that has MPEG-2 as part of its title.

I have not connected to a cable yet - just trying to get the software installed and hdw setup. 

I assume that the lack of response for my remote control is related to this.

Where do I go from here?

/Roger

Are you trying to set up the atsc part or the analogue part of the card?

---

### Post by linux.rog on 2011-10-20
Nickrout & thatguruguy,

Input is from a QIP 7100 series set top box via an S-video cable. Connecting the cable didn't seem to make a difference. I still get the same error - can't connect to backend server.

Backend setup shows Probed Info as Hauppague 1600 [cx18] appended on the for some card types. I've tried them all to no avail. Maybe the problem is somewhere else?

Thanks for looking into this.

---

### Post by thatguruguy on 2011-10-20
Could you post the tail end of your backend log?

---

### Post by linux.rog on 2011-10-20
Here tis after a re-boot. (channel services not subscribed to as of yet).

/Roger


2011-10-20 22:30:39.163 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org](www.mythtv.org)
2011-10-20 22:30:39.206 Using runtime prefix = /usr
2011-10-20 22:30:39.244 Using configuration directory = /home/mythtv/.mythtv
2011-10-20 22:30:39.275 Empty LocalHostName.
2011-10-20 22:30:39.297 Using localhost value of mythtv
2011-10-20 22:30:39.365 New DB connection, total: 1
2011-10-20 22:30:39.393 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:39.433 Closing DB connection named 'DBManager0'
2011-10-20 22:30:39.456 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:39.540 Current locale EN_US
2011-10-20 22:30:39.606 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-10-20 22:30:39.668 Current MythTV Schema Version (DBSchemaVer): 1264
2011-10-20 22:30:39.735 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-10-20 22:30:39.813 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-10-20 22:30:39.865 MythBackend: Starting up as the master server.
2011-10-20 22:30:39.942 New DB connection, total: 2
2011-10-20 22:30:39.981 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:40.058 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2011-10-20 22:30:40.139 ChannelBase(2) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-10-20 22:30:40.199 MythBackend, Warning: No valid capture cards are defined in the database.
2011-10-20 22:30:40.223 New DB scheduler connection
2011-10-20 22:30:40.248 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:40.304 Scheduler, Warning: Listings source '' is defined, but is not attached to a card input.
2011-10-20 22:30:40.331 Scheduler, Error: No channel sources defined in the database
2011-10-20 22:30:41.094 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org](www.mythtv.org)
2011-10-20 22:30:41.106 Using runtime prefix = /usr
2011-10-20 22:30:41.131 Using configuration directory = /home/mythtv/.mythtv
2011-10-20 22:30:41.157 Empty LocalHostName.
2011-10-20 22:30:41.198 Using localhost value of mythtv
2011-10-20 22:30:41.266 New DB connection, total: 1
2011-10-20 22:30:41.293 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:41.317 Closing DB connection named 'DBManager0'
2011-10-20 22:30:41.340 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:41.383 Current locale EN_US
2011-10-20 22:30:41.415 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-10-20 22:30:41.457 Current MythTV Schema Version (DBSchemaVer): 1264
2011-10-20 22:30:41.484 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-10-20 22:30:41.511 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-10-20 22:30:41.540 MythBackend: Starting up as the master server.
2011-10-20 22:30:41.575 New DB connection, total: 2
2011-10-20 22:30:41.599 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:41.625 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2011-10-20 22:30:41.649 ChannelBase(2) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-10-20 22:30:41.673 MythBackend, Warning: No valid capture cards are defined in the database.
2011-10-20 22:30:41.699 New DB scheduler connection
2011-10-20 22:30:41.740 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:41.791 Scheduler, Warning: Listings source '' is defined, but is not attached to a card input.
2011-10-20 22:30:41.823 Scheduler, Error: No channel sources defined in the database
2011-10-20 22:30:42.975 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org](www.mythtv.org)
2011-10-20 22:30:42.982 Using runtime prefix = /usr
2011-10-20 22:30:43.032 Using configuration directory = /home/mythtv/.mythtv
2011-10-20 22:30:43.074 Empty LocalHostName.
2011-10-20 22:30:43.165 Using localhost value of mythtv
2011-10-20 22:30:43.226 New DB connection, total: 1
2011-10-20 22:30:43.276 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:43.309 Closing DB connection named 'DBManager0'
2011-10-20 22:30:43.332 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:43.358 Current locale EN_US
2011-10-20 22:30:43.382 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-10-20 22:30:43.420 Current MythTV Schema Version (DBSchemaVer): 1264
2011-10-20 22:30:43.451 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-10-20 22:30:43.478 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-10-20 22:30:43.507 MythBackend: Starting up as the master server.
2011-10-20 22:30:43.533 New DB connection, total: 2
2011-10-20 22:30:43.557 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:43.584 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2011-10-20 22:30:43.607 ChannelBase(2) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-10-20 22:30:43.632 MythBackend, Warning: No valid capture cards are defined in the database.
2011-10-20 22:30:43.657 New DB scheduler connection
2011-10-20 22:30:43.682 Connected to database 'mythconverg' at host: localhost
2011-10-20 22:30:43.708 Scheduler, Warning: Listings source '' is defined, but is not attached to a card input.
2011-10-20 22:30:43.732 Scheduler, Error: No channel sources defined in the database

---

### Post by nickrout on 2011-10-21
> 2011-10-20 22:30:40.139 ChannelBase(2) Error: InitializeInputs():
Could not get inputs for the capturecard.
Perhaps you have forgotten to bind video
sources to your card's inputs?
You have not completed all of the setup steps in mythtv-setup. I suggest you read the documentation again.

---

### Post by linux.rog on 2011-10-21
I've read and re-read docs at Mythbuntu.org, stepping thru the setup multiple times. I don't see a step that corresponds to "binding" in either front or backend setup.

It is also unclear WHICH capture card to choose (see original post).

Thanks for helping to move me along.

---

### Post by nickrout on 2011-10-21
> **linux.rog said:**
> I've read and re-read docs at Mythbuntu.org, stepping thru the setup multiple times. I don't see a step that corresponds to "binding" in either front or backend setup.

It is also unclear WHICH capture card to choose (see original post).

Thanks for helping to move me along.

For analogue it will be IVTV-MPEG2 encoder card I think. Don't forget the othre stages too - set up a video source, bind it to the capture card etc etc

---

### Post by linux.rog on 2011-10-21
OK, managed to get rid of backend connect fail. Still having problems, e.g., no response to IR, etc.

I have the following setup in mythbackend
Capture card:
IVTV MPEG-2 encoder card
Video device /dev/video24
Probed info Hauuppauge HVR-1600 [cx18]
Default input tuner 1

the latter seems to match up with having S-video from my set top box to the capture card.

I've posted the tail of logs (people do not have to look at a lot of "stuff") here:
    [www.bronord.com/backend.log]("http://www.bronord.com/backend.log")
    [www.bronord.com/frontend.log]("http://www.bronord.com/frontend.log")
(Tried to upload these but got "invalid file" error)

Obviously I'm still having trouble understanding the meaning of the various dialogs. 

I know the channel stuff is due to not having a source for channel lineups defined and I'm not yet connected to the Internet on the mythbuntu box.

Thanks for your patient help.

From your antipod (almost), /Roger

---

### Post by nickrout on 2011-10-22
> **linux.rog said:**
> OK, managed to get rid of backend connect fail. Still having problems, e.g., no response to IR, etc.

I have the following setup in mythbackend
Capture card:
IVTV MPEG-2 encoder card
Video device /dev/video24



probably not correct, try /dev/video0> 
Probed info Hauuppauge HVR-1600 [cx18]
Default input tuner 1

the latter seems to match up with having S-video from my set top box to the capture card.

I've posted the tail of logs (people do not have to look at a lot of "stuff") here:
    [www.bronord.com/backend.log]("http://www.bronord.com/backend.log")
    [www.bronord.com/frontend.log]("http://www.bronord.com/frontend.log")
(Tried to upload these but got "invalid file" error)

Obviously I'm still having trouble understanding the meaning of the various dialogs. 

I know the channel stuff is due to not having a source for channel lineups defined and I'm not yet connected to the Internet on the mythbuntu box.



you haven't completed setup then. Read the docs, listen to the help you are getting, you must complete all the steps.> 
Thanks for your patient help.

From your antipod (almost), /Roger

---

### Post by linux.rog on 2011-10-22
I have tried /dev/video0.

Don't understand what I have not yet done and have poughed thru. Don't see what I've not setup.

Giving up for now - wife thinks I'm nutz. She's probably correct.

---

### Post by nickrout on 2011-10-22
After setting up the capture card you need to set up a video source, then an input connection then scan for channels.

---

### Post by linux.rog on 2011-10-29
> **nickrout said:**
> After setting up the capture card you need to set up a video source, then an input connection then scan for channels.

I ran thru the setup again, doing the steps you mentioned, including using /dev/video0. And, I scanned from listing source - I'm using scheduels direct - and this appeared to "go."

When I "watch tv," I get a large, green rectangle. No response from my remote.

The backend log shows an error
    Channel(/dev/video0) Warning: You have not set an external channel changing script for a composite or s-video input. Channel changing will do nothing.

The wiki suggested going to [http://www.mythtv.org/wiki/Change-channel-lirc.pl](http://www.mythtv.org/wiki/Change-channel-lirc.pl)
Is "change-channel-lirc.pl" the script of choice? I do not find it on my PC. If I create it, where does it go? What permissions?

I am also having problem with spill-over beyond the bounds of my screen - the image is a few pixels too big all around. I can find no setting to change this. Do you know where it's at?

I will post a separate thread on the remote / IR issues.

Logs (tails) and conf files are posted at [http://www.bronord.com/myth](http://www.bronord.com/myth): back- and frontend logs, syslog, dmseg, lircd.conf, hardware.conf

---

### Post by linux.rog on 2011-11-01
I feel abandoned. NO REPLY for a some days, even tho the topic seems to be of interest (317 views) :(. No response to separate thread on IR (29 views).

I've managed to get a picture but not good. Image is out-of-bounds. No sound. No IR. Frustrated by opaque setup screens ](*,).  Sigh:confused:.

---

### Post by klc5555 on 2011-11-01
> **linux.rog said:**
> I ran thru the setup again, doing the steps you mentioned, including using /dev/video0. And, I scanned from listing source - I'm using scheduels direct - and this appeared to "go."

When I "watch tv," I get a large, green rectangle. No response from my remote.

The backend log shows an error
    Channel(/dev/video0) Warning: You have not set an external channel changing script for a composite or s-video input. Channel changing will do nothing.

The wiki suggested going to [http://www.mythtv.org/wiki/Change-channel-lirc.pl](http://www.mythtv.org/wiki/Change-channel-lirc.pl)
Is "change-channel-lirc.pl" the script of choice? I do not find it on my PC. If I create it, where does it go? What permissions?



You can use either the perl script (change-channel-lirc.pl) or the bash script. The bash script is a bit slower, but I find it more reliable. Either script goes in /usr/bin ; just mark it as + executable (chmod +x) The path to the script will be eventually entered in the Input Connections menu for the particular tuner you're trying to set up. But hold off on this stuff for the moment.

At this stage you're not trying to change channels, you're just trying to get some kind of a signal through your box. Fortunately, there is no requirement to scan for analog input channels in Mythtv, just digital. So when you have your Video Source bound to your Input Connections, go into the Channel Editor menu and Add a single channel manually. Just set it at channel 3 and name it whatever you want. Go back into Input Connections and set this dummy "channel 3" as your startup channel for this card. 

Now exit the setup, make sure your cable box is hooked to the cable from the outside world and is also hooked to your 1600 card through the s-cable. Start the myth backend and frontend, and start "Live TV". Tune your cable box to known good channels using whatever sort of remote the cable people gave you, and if your cable box itself is live, then you should be getting TV on Mythtv on dummy "channel 3" --TV of whatever station you happened to have manually tuned the cable box to.

If you do have a live signal, then it will be time to start worrying about nonsense like LIRC and channel changing scripts. Let's hope this is what we get.

 If, however, you're still confronted with something like a green or red rectangle (not even static) then the odds are either you have the kernel-level cx18 driver loading with incorrect module parameters for your particular flavor of the 1600 (there are a lot of them), or (if it's a really really new model) it may not be supported yet in the stock Linux kernel and may require a patched driver from the cx18 developers over at linuxtv.org

---

### Post by linux.rog on 2011-11-01
Thanks you, klc5555.  In the meantime I am going to totally re-install Mythbuntu. I think starting with a clean slate may be useful . . . ploughing thru all of the menus once again.

I like your idea about trying to get a live channel and going from there.

My wife keeps asking if I've made any progress and looks at my face and the TV pulled out from the wall and knows the answer.

Physical connections:
I'm taking output from my STB via s-video into the capture card and connecting via S-video-1 in software.. Sound from separate outputs from the STB into the audio input on the capture card. Might I be better off taking a coax from the STB into the capture cards cable-in connection? Too bad I did not recognize in advance that this card will not do HD with the setup that I have - no HDMI or firewire input. (Recall I need the STB to decode encrypted signals.)

Like you said, I'll concentrate on getting a picture first.

/Roger

---

### Post by nickrout on 2011-11-02
> **linux.rog said:**
> Thanks you, klc5555.  In the meantime I am going to totally re-install Mythbuntu. I think starting with a clean slate may be useful . . . ploughing thru all of the menus once again.

I like your idea about trying to get a live channel and going from there.

My wife keeps asking if I've made any progress and looks at my face and the TV pulled out from the wall and knows the answer.

Physical connections:
I'm taking output from my STB via s-video into the capture card and connecting via S-video-1 in software.. Sound from separate outputs from the STB into the audio input on the capture card.Start with the basics. Try ```
mplayer /dev/video0
``` and see if there is anything working.>  Might I be better off taking a coax from the STB into the capture cards cable-in connection? No, definitely not.> Too bad I did not recognize in advance that this card will not do HD with the setup that I have - no HDMI or firewire input. (Recall I need the STB to decode encrypted signals.)If you want HD you need an HDPVR > 

Like you said, I'll concentrate on getting a picture first.

/Roger

---

### Post by klc5555 on 2011-11-02
> **linux.rog said:**
> Thanks you, klc5555.  In the meantime I am going to totally re-install Mythbuntu. I think starting with a clean slate may be useful . . . ploughing thru all of the menus once again.

I like your idea about trying to get a live channel and going from there.

My wife keeps asking if I've made any progress and looks at my face and the TV pulled out from the wall and knows the answer.

Physical connections:
I'm taking output from my STB via s-video into the capture card and connecting via S-video-1 in software.. Sound from separate outputs from the STB into the audio input on the capture card. Might I be better off taking a coax from the STB into the capture cards cable-in connection? Too bad I did not recognize in advance that this card will not do HD with the setup that I have - no HDMI or firewire input. (Recall I need the STB to decode encrypted signals.)

Like you said, I'll concentrate on getting a picture first.

/Roger

1)If you can do coax from the settop box to the 1600, that is always a better option than s-video. I checked the online manual for the QIP 7100, and you should be able to connect coax from connection "2" in the back of the settop box that will output on analog channel 3 or 4 to your 1600. Pick one, and then set your analog 1600 to start on that channel when you set up the backend. Also check the connections on the back of your 1600 card. It's easy to hook to the wrong one --I do it frequently.

2)The cable companies, even Verizon, are required to provide the locals in clear QAM. So you should have some digital TV available to you in the clear. Possibly in HD. This will require setting up a second Video Source that will eventually store your digital channels. And of course a coax splitter ahead of the cable box to bypass the settop box and provide direct cable input into your card's digital input. Going to the following site and entering your zip code should give you an idea of what's available in the clear on the various cable carriers in your area: [http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/)

3) I'm more concerned about your green screen on the model 1199 of the Hauppauge 1600. The tuner model number is stamped on the tuner of the card. Model 1199 (74301) has been reported as having difficulties since it was introduced a year or so ago. (Basic information here: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600) ) Some of difficulties apparently persist, since there's a fair amount of message traffic with the driver developer about the 74301 as recently as this summer. [http://www.gossamer-threads.com/lists/ivtv/users/41426](http://www.gossamer-threads.com/lists/ivtv/users/41426) None of these difficulties, however, seem to center around "green screen"

As an aside, when buying Hauppauge 1600s, the older the better (since support bugs have been worked out). It's usually least expensive to buy the used ones that Windows users dump because the Windows drivers can't do clear QAM with them (models 74031 and 74551). They work perfectly now in Linux, including QAM.

But late-model difficulties seem to affect only the analog tuner. For this reason it may be easier going at first to set up the digital side of your card (on its own Video Source), hooking the digital half of your card directly to the cable (no box) and running a channel scan for whatever clear QAM local traffic Verizon may be pumping down the cable. The scan will show nearly 0% signal strength, but as long as it starts getting occasional locks as it scans upward through the 50s 60s and 70s, you've got actual QAM signals. This may give you your first success.

---

### Post by nickrout on 2011-11-02
> **klc5555 said:**
> 1)If you can do coax from the settop box to the 1600, that is always a better option than s-video. 

Absolute rubbish. s-video will be better quality.

---

### Post by klc5555 on 2011-11-02
> **nickrout said:**
> Absolute rubbish. s-video will be better quality.

OK, well, once he gets the card running in any context, he can move from analog input to S-video.

---

### Post by linux.rog on 2011-11-02
FIRST: I have difficulty with setup screens, etc., because the edges are beyond the bounds of my TV screen. Can not adjust this with my TV settings. Is there a CLI approach? I see nothing under the various SETTINGS.

Card support: At [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)
they say there's a kernel patch for 74301 and 74321 accepted upstream and support will be available in the 2.6.39 kernel. Mythbuntu 11.10 is running kernel 3.0.0-12-generic. I hope this means the problem is past?

I re-installed 11.10 including all patches. Connected analog coax out of STB to capture card's "TV Connector for Cable TV." I'm using HDMI from my video card to TV input. I ran thru setup, without channel scan. Added channel 3 manually as well as setting it as first channel to tune. I can get an image THIS WAY, from the cli, with a ^c after a few seconds and before running vlc:
    cat /dev/video0 > ~/movie.mpg
    vlc /~/movie.mpg
I see the bit of programming captured before the ^c on that is showing on the channel selected on my STB. No sound.

Watch TV gives no sound or picture BUT this:

1: Tuner 1
Unknown
<some time stuff here>
    3 Signal 0%|(FDNoLock
    1000

My setup:
Card type IVTV MPEG-2 encoder card
video: /dev/video0

Video source - Input Connections
  MPEG: /dev/video0} (Tuner1) Cable    (The name I gave it)
 ...eset tuner to channel:3   (I can not see the beginning of this line)
starting chanel:3

I saw the discussion about S-video. Will stick w/ this for awhile (I disconnected the s-vid and sound cables.)

Thanks to both advisers. Now, off to eat dinner and an evening dance to de-stress from Mythbuntu! :-\"

---

### Post by nickrout on 2011-11-02
> **klc5555 said:**
> OK, well, once he gets the card running in any context, he can move from analog input to S-video.

Well your approach leads to the complexity of having to tune the tuner card to an analogue channel, and then tune the STB. A very odd and frankly bad approach.

---

### Post by nickrout on 2011-11-02
> **linux.rog said:**
> FIRST: I have difficulty with setup screens, etc., because the edges are beyond the bounds of my TV screen. Can not adjust this with my TV settings. Is there a CLI approach? I see nothing under the various SETTINGS. you have overscan. if you can't fix that then plug in a monitor until you get it all set up.> 

Card support: At [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)
they say there's a kernel patch for 74301 and 74321 accepted upstream and support will be available in the 2.6.39 kernel. Mythbuntu 11.10 is running kernel 3.0.0-12-generic. I hope this means the problem is past?

I re-installed 11.10 including all patches. Connected analog coax out of STB to capture card's "TV Connector for Cable TV." I'm using HDMI from my video card to TV input. I ran thru setup, without channel scan. Added channel 3 manually as well as setting it as first channel to tune. I can get an image THIS WAY, from the cli, with a ^c after a few seconds and before running vlc:
    cat /dev/video0 > ~/movie.mpg
    vlc /~/movie.mpg
I see the bit of programming captured before the ^c on that is showing on the channel selected on my STB. No sound.

Watch TV gives no sound or picture BUT this:

1: Tuner 1
Unknown
<some time stuff here>
    3 Signal 0%|(FDNoLock
    1000

My setup:
Card type IVTV MPEG-2 encoder card
video: /dev/video0

Video source - Input Connections
  MPEG: /dev/video0} (Tuner1) Cable    (The name I gave it)
 ...eset tuner to channel:3   (I can not see the beginning of this line)
starting chanel:3

I saw the discussion about S-video. Will stick w/ this for awhile (I disconnected the s-vid and sound cables.)

Thanks to both advisers. Now, off to eat dinner and an evening dance to de-stress from Mythbuntu! :-\"

---

### Post by klc5555 on 2011-11-03
> **linux.rog said:**
> FIRST: I have difficulty with setup screens, etc., because the edges are beyond the bounds of my TV screen. Can not adjust this with my TV settings. Is there a CLI approach? I see nothing under the various SETTINGS.

Card support: At [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)
they say there's a kernel patch for 74301 and 74321 accepted upstream and support will be available in the 2.6.39 kernel. Mythbuntu 11.10 is running kernel 3.0.0-12-generic. I hope this means the problem is past?

I re-installed 11.10 including all patches. Connected analog coax out of STB to capture card's "TV Connector for Cable TV." I'm using HDMI from my video card to TV input. I ran thru setup, without channel scan. Added channel 3 manually as well as setting it as first channel to tune. I can get an image THIS WAY, from the cli, with a ^c after a few seconds and before running vlc:
    cat /dev/video0 > ~/movie.mpg
    vlc /~/movie.mpg
I see the bit of programming captured before the ^c on that is showing on the channel selected on my STB. No sound.

Watch TV gives no sound or picture BUT this:

1: Tuner 1
Unknown
<some time stuff here>
    3 Signal 0%|(FDNoLock
    1000

My setup:
Card type IVTV MPEG-2 encoder card
video: /dev/video0

Video source - Input Connections
  MPEG: /dev/video0} (Tuner1) Cable    (The name I gave it)
 ...eset tuner to channel:3   (I can not see the beginning of this line)
starting chanel:3

I saw the discussion about S-video. Will stick w/ this for awhile (I disconnected the s-vid and sound cables.)

Thanks to both advisers. Now, off to eat dinner and an evening dance to de-stress from Mythbuntu! :-\"

The fact that you get viewable output from cat /dev/video0  shows that the analog tuner is being loaded satisfactorily. So the driver appears to be OK. Hurrah!

In setting up your settop box as an ordinary analog input on channel 3 (without scanning), don't forget to actually add a channel 3 in the Channel Editor for the 1600 to start on. For the time being, this channel 3 is where you'll assign it on the first page of the Add dialogue in Channel Editor, and "3" is what you'll put (for the time being) for "frequency or channel" in about p. 3 of that same dialogue. Mythtv and your 1600 do not require you to specify any tuning frequencies or similar for tuning to analog channels: the channel number is sufficient. 

Eventually, once you have signals that are both viewable and hearable in Mythtv, and feel a bit more comfortable maneuvering around in creating new Video Sources and such, you probably will want to switch your configuration over to s-video. nickrout is absolutely correct, of course, about s-video's improvement of quality over analog input to the SD level, and it might have the added benefit of helping to keep his blood pressure down. ;)

I also agree with nickrout that you'll likely do better with a monitor until things are set up better and can fix the overscan. In this scenario, your sound likely will be coming from your sound card through ordinary stereo audio cables.

---

### Post by linux.rog on 2011-11-03
Well, wanting to do the good thing, I deleted all capture cards, etc., in backend. Hooked up S-video out on my STB to S-video in on capture card. One step forward, two back-ards.

I now get a redish blob using the cat /dev/video0 approach. Watch TV gives a similar result as before, that is, text similar to what was outlined previouly, followed in a few seconds by the blob. Of course we get no sound but I note that logs show some evidence of sound-stuff on the capture board and my understanding is that S-video transmits sound from the STB.

I deleted the old channel 3 - it was x-out and added it again. My setup now:


Card type IVTV MPEG-2 encoder card
video: /dev/video0
default input: S-Video 1

Video source: Cable S-Video (Name I gave it)

Input connections
Capture Device [MPEG: /dev/video0]
Input: S-Video
Video Source: Cable S-Video
Preset to channel 3

Channel editor
Added new channel 3
Video source: Calble S-Video
TV format: default
.
.
Frequency or Channel: 3

Logs and dmesg are at [http://www.bronord.com/mythlogs](http://www.bronord.com/mythlogs)

Thanks again for your patience.

P.S. You were right about using a monitor: now I can see the whole screen. Of course my living room looks like the control room for a mainframe computer with a wire management problem.

---

### Post by nickrout on 2011-11-04
> **linux.rog said:**
> Well, wanting to do the good thing, I deleted all capture cards, etc., in backend. Hooked up S-video out on my STB to S-video in on capture card. One step forward, two back-ards.

I now get a redish blob using the cat /dev/video0 approach.In the command line approach, what are you doing to switch to the s-video input. It's a while since I used an analogue card, but I think v4lctl can be used to switch a whole lot of option, and may be needed to switch inputs before doing mplayer /dev/video0>  Watch TV gives a similar result as before, that is, text similar to what was outlined previouly, followed in a few seconds by the blob. Of course we get no sound but I note that logs show some evidence of sound-stuff on the capture board and my understanding is that S-video transmits sound from the STB.

I deleted the old channel 3 - it was x-out and added it again. My setup now:


Card type IVTV MPEG-2 encoder card
video: /dev/video0
default input: S-Video 1
what other inputs are mentioned in mythtv-setup> 
Video source: Cable S-Video (Name I gave it)

Input connections
Capture Device [MPEG: /dev/video0]
Input: S-Video
Video Source: Cable S-Video
Preset to channel 3

Channel editor
Added new channel 3
Video source: Calble S-Video
TV format: default
.
.
Frequency or Channel: 3

Logs and dmesg are at [http://www.bronord.com/mythlogs](http://www.bronord.com/mythlogs)

Thanks again for your patience.

P.S. You were right about using a monitor: now I can see the whole screen. Of course my living room looks like the control room for a mainframe computer with a wire management problem.

so what do your backend and frontend logs say when trying to get a channel?

---

### Post by linux.rog on 2011-11-04
WHOA! I gotta picture, both from /dev/video0 and with Watch TV with MythFrontend. :!:

What did I do? Hocus Pocus. Rebooting? I don't think so since I did that yesterday after setting up. I also ran thru mythbackend to review settings but changed none.

I see a pic on my monitor (VGA connection)  and on the TV with HDMI connection). Both from my video card. Thus I'm skipping the latest suggestions from nickrout.

SO: next step? To do:
[INDENT]cure overscan (I'll google this)
get IR working
sound
[/INDENT]I see channel scanning coming later. I had a trial subscription to Schedules Direct but it ran out and, of course, all the info scanned for that disappeared when I re-installed.

Is it better to start a new thread - Master Backend Connect Fails is long past. Maybe: Setup HVR-1600 - however, I do see 480 views so there must be some interest on this subject.

P.S. Where do the "values" of the various parameters get stored - what files? This info might be useful for those who try to setup an HVR-1600 1199/74301 in the future.

/Roger

---

### Post by klc5555 on 2011-11-04
> **linux.rog said:**
> WHOA! I gotta picture, both from /dev/video0 and with Watch TV with MythFrontend. :!:

What did I do? Hocus Pocus. Rebooting? I don't think so since I did that yesterday after setting up. I also ran thru mythbackend to review settings but changed none.

I see a pic on my monitor (VGA connection)  and on the TV with HDMI connection). Both from my video card. Thus I'm skipping the latest suggestions from nickrout.

SO: next step? To do:
[INDENT]cure overscan (I'll google this)
get IR working
sound
[/INDENT]I see channel scanning coming later. I had a trial subscription to Schedules Direct but it ran out and, of course, all the info scanned for that disappeared when I re-installed.

Is it better to start a new thread - Master Backend Connect Fails is long past. Maybe: Setup HVR-1600 - however, I do see 480 views so there must be some interest on this subject.

P.S. Where do the "values" of the various parameters get stored - what files? This info might be useful for those who try to setup an HVR-1600 1199/74301 in the future.

/Roger

Congrats! Each success is progress.

Almost everything pertaining to "values" in mythtv gets stored in the mysql database "mythconverg". There are a few things that may get run directly from the OS.

I can't help you with sound through HDMI --not my thing. But check whether you have any sound at all (through alsa:default) by hooking the sound card to a set of PC speakers (or just test with a set of ipod earphones). Check both front and back panels --sometimes sound initially gets routed through one, but not the other. Check your alsa mixer to make sure the thing is not muted, and it's using your sound card as the default (rather than, say, the sound decoder chip in your video card). The command aplay -l should give you a list of the sound devices that alsa knows about. Sometimes Intel surround-sound digital/analog boards are not initially detected without a bit of configuration of how the module loads.

I confess I eventually gave up trying to get the IR working on the various 1600s I own that have a blaster, and came to use a 3rd-party USB unit instead: an IguanaWorks model which I have had very good luck with (I now own three of them). The IR blaster driver for the 1600 card's own blaster was not entirely functional at the time, and was being recoded over from a similar IR blaster in hauppauge PVR 150. This was a couple of years ago and the hauppauge driver is likely to be better by now.

Good luck! You're on your way!

---

### Post by linux.rog on 2011-11-07
The original issue of master backend connect failure has been solved, along with a few other mysteries.

Thanks to nicrout and klc5555.

/Roger

---

