---
title: "Capture video triggered by movement, upload to server, watch online"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by Cubytus on 2012-01-28
Hello all, 

I'm looking to re-purpose a quite old PC (P4) as a **home** surveillance device. It's noisy as hell, and packs a quite small hard drive (80GB) that's further shared between Windows XP and Ubuntu 11.10, as I still try to examine the solutions available on each platform. To it, a very old webcam is connected (manual focus, 640x480@7.5fps max). It's connected to a standard home Internet connection, capable of ~700KBps upload, but computer is not accessible from the Web. On the Web side I have access to: ~8GB of WebDAV or FTP storage, connected to a HTTP web server. Also, around 2GB of Dropbox storage and 25GB of Windows-only storage (not SkyDrive, but appears as a network disk).

Since hard drive space is limited and that it would be pretty uninteresting to watch a fixed picture (hopefully), even in fast-forward, I would like the computer to record full-motion, full quality video clip for a few seconds before movement occured, as well as about 30 min after first trigger, resetting the countdown each time a movement is recorded, then return to standby. Since no animal live in my home, no movement at all is expected (I like pets, but would find irresponsible to have one since I don't have the time to take care of them).

But at the same time, I would like this computer to capture still pictures, say, 5 a second, and upload them to a server. The reason is, I noticed that an AVI-encoded flux tends to get pretty big, and I'm not sure the computer packs enough power to compress an MP4 in realtime, especially as I hope to add a second webcam. Besides, the Internet connection wouldn't be able to push a large file in (near) realtime, whereas even maximum quality JPEGs can be uploaded in no time. If multiple movement occurence is to be recorded, I would like it to start recording a second file. Would it be possible to incrementally record a file, or automatically merge smaller segments? I noticed that it's not always feasible or practical to merge numerous small segments. Finally, I would like it to backup the recorded file to FTP, Dropbox, or WebDAV server; is it feasible?

But the most important part would be on the Web side. I want to be able to see the video as it's being captured, or stored on the server indefinitely for future review. On Windows, a few surveillance suites are able, on movement trigger, to 1- send an email 2- send an SMS, 3- act as a Web server to remotely view what's being recorded 4- send the resulting file to a server. Major drawbacks is they usually require expensive subscription and rely on fossil technologies such as ActiveX. How can I get a webpage to successively display snapshots so as to make a pseudo-animated stream? I would like it to show, in one form or another, the different sequences it captured so I can review them at will.

So far, I noticed that Camorama could at least do a part of what I'm looking for, but is clearly missing on Web's side. Is there a software that could do what I'm looking for, all in one? Or a web page model that could automaatically display what I'm looking for? Ultimate goal would be efficiency.

Do ask for precision or put up suggestions, as this description may not be perfectly clear.

---

### Post by SteveDee on 2012-01-28
> **Cubytus said:**
> ...1. Is there a software that could do what I'm looking for, all in one?

2. Ultimate goal would be efficiency.

1. I don't know. But I can suggest you look at Kenneth Lavrsen's excellent application: motion
I use it to monitor wildlife, and some of the features I use include:-
motion capture;
 - it can detect movement based upon whole image, zones or even a mask.
 - It can save both JPG and video.
 - It can start saving a few frames before the event and a few frames after.
 - It can link video where more movement is detected within a time frame (default 60s).

Web server & monitoring; 
 - it includes a simple web server. I only use this across a local network.
 - monitor/view live video via a remote web browser.
- I also review captured video via the network, and delete unwanted files.
 - I run Motion on a headless Lubuntu pc

2. I doubt whether the word "efficiency" can be applied to your noisy old computer. If this is to run 24/7 you need a quiet, fan-less, low power consumption system. Take a look at Raspberry Pi which is due for release in a few weeks.

Also, high quality video takes a lot of space and may not be necessary if you only have a low quality webcam.

On Linux you may find you can only connect one webcam to one USB controller due to bandwidth limitations. Note that you may have 4 or 5 USB sockets, but if they run into a single controller you may have problems.

The quality of JPG & video on Motion is configurable.

Don't be put off by the lack of a User Interface, as Motion uses a configuration file to set all variables. You can also use your web browser to change settings. For efficiency, if you are running more than one camera, Motion runs additional "threads" for each camera, each allowing individual config settings.

You can install Motion via Synaptic.

I hope this is of some help.

++++++
Edit: Motion Home Page: [http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome)

---

### Post by Cubytus on 2012-01-28
Efficiency is about my time, not the computer's time. I don't want to spend hours trying to extract a video that will, hopefully, be completely uneventful. Besides, the repeated thefts have cost me upward of 3 low-quality computers, so I just had to beg for whatever lab members had as a disused computer. Thanks for the advice on Raspberry Pi, but "due in a few weeks" isn't interesting, I'll have a look at what is available *now*.

From your short description, motion seems to pack a good part of what commercial solutions tend to boast. 
Can *motion* **upload** to a web server? I don't care much about a local web server since if the computer is stolen, recordings disappear. Local network/web control is nice, but I'm not yet familiar with command-line-only Ubuntu, as I can't yet remember where each file is located, what each command flag does. It all boils down to my crappy memory.

Speaking of which... How can I log in remotely from the login screen? SSH server only activates after login.

---

### Post by SteveDee on 2012-01-28
> **Cubytus said:**
> ...the repeated thefts have cost me upward of 3 low-quality computers....

Really sorry to hear that. Maybe it would be better to chain your computer to the radiator in your room than try to capture video evidence.

I don't know how to publish, you'd have to research that.

Although there is no GUI with motion, you don't need to remember lots of command line stuff. You can set it to start when your computer starts. The config file can be edited with a text editor.

---

### Post by Cubytus on 2012-01-28
Actually, it was about the stolen value. I only had one laptop computer until then, that I took along every time (a habit I kept from the time I had no fixed place to sleep).

Since this computer is extremely slow and unreactive under Ubuntu, I may end up trying the alternate version. I'm just not familiar at all at managing software and config from the command line, especially on a headless machine.

But remote storage for capture is definitely a requirement.

---

### Post by goodbye-windows(tm) on 2012-07-27
> **SteveDee said:**
> Maybe it would be better to chain your computer to the radiator in your room than try to capture video evidence.


I was thinking along the same lines. Think low power/stealth though.

We have a house in a rural area. If the doors are locked, we live far enough away from everyone else that thieves could literally drive a skidder through a wall to gain access and could stay in the house for hours, even invite friends and have a party there.

Our house was broken into, they took almost everything, except the computer. I run my computers with harddrives outboard, hanging on the cable  and at least one side removed. I have a business card from the local computer repair shop pasted to the front of the computer. And, a note to Paula, telling her that the computer is still down. 

So, the thieves passed up a perfectly running desktop. 

If you run your security application(s) without a monitor connected, and one side panel removed, you won't need a fan on your processor, so a bad guy wouldn't have any idea the computer was on (use a very low resolution camera to feed to the computer to determine if there's an intruder) . With a low res camera the processor load will be very very light so no fans are needed. When the computer senses an intruder, it can turn on a high res camera (with it's own onboard sdcard type memory). Bubble gum cams are selling for $10.99 on ebay, check youtube for mods to make it see in the dark and to check out the video quality of the thing.

My next project will be to mount a laptop in the dehumidifier in the basement. There's all kinds of room there, and lots of power available. And no one would even think of it containing a security system.

I also have some ideas for stealth zero false positive alarms using wireless links to the alarm system.

Anyway, I digress, sorry.

Enjoy.

Art

---

### Post by Cubytus on 2012-07-27
I have a sense for neat places, so would find that kind of computer unsightly. Even, I wouldn't dare run a P4 without fan. Recording video from 4 cameras require a LOT of computing power. I understand about a low-res camera turning on the others, but the software I use doesn't allow that. Each camera is independently controlled. The closest I could find was to use the microphone as a trigger, although living in an apartment, I guess a would-be intruder would be smart enough not to make big noise.

The solution I kept is based around an i3 HP g60 laptop, since the old P4 definitely didn't have the necessary power and stability to support 4 "bubble-gum" video cameras, even at 5 fps each. Even just running Windows XP on an underclocked CPU made it crash in about 20 minutes when ambient temp went over 27°C (pretty much every day, in summer) and fan was limited to 50% rotation speed using software. There's a reason why P4 where nicknamed "toasters". At speed, it sounds as sitting in a Boeing near the wings.

 I count on the HP being mauve (= hard-to-resell color), countless cables hanging from it, and it being fast enough to send alerts for potential thieve not taking the care of taking it, or at least be able to have recordings anyway. I'm hesitant to partly dismantle a perfectly fine laptop, as it's not as clean or easy than on desktops. I like the laptop because if the thief removes the fuse, it will be still recording for a while.

My place isn't large, and all cables would remain in plain sight even if the laptop is hidden (under the chest). I still would need a monitor to control and run the security application and have a look at live recordings. There's a large constraint due to power outlet localization and cables length and camera positions.

Software is Windows 7 Pro with Blue Iris. I just couldn't manage to make Ubuntu run on this g60, and needed to get recording working.

Sure, it could be made better, but I don't know how exactly.

---

### Post by goodbye-windows(tm) on 2012-07-27
OK, I understand now. 

It sounds like your system works, which is more than I can say for mine.

I keep bouncing back and forth between a garden variety home security system and the dumbed down linux computer running in stealth mode.

Regarding cables, al la stealth.....

I have experimented with #30 and #36 magnet wire, twisted at about 15 to 25 turns per foot. It's very cheap and is practically invisible if it's painted to match the surroundings. It's legal to use it for low voltage power lines provided there is a fuse at the point where the power line transitions to the magnet wire line. 

I even ran my dsl through it, and it worked just fine. Most small cameras don't pull more than 12 ma dc (average).

I think your system requires a supercomputer because you're insisting on having video in a buffer, so your computer does allot of crunching data just to save the video buffer.

If you ever decide to scale down your security system, look at bubble gum cams and check out the pic-list, those guys do some amazing things with PIC chips. Someone might have written some code that scans video for changes in the screen view.  If you use bubble gum cams, the storage for the video is built into the units directly. By doing so, the need for a computer is greatly diminished.

My P4 runs cool with just a heatsink provided the processor load is kept under 15 percent. I think I could improve on that by adding a custom heatsink made out of copper instead of aluminum. 

I have a ham radio license, so I have many options for data transmission of the alarm signals, I'm not planning to use the internet to warn me of an intrusion.

GL and congrats on getting your system running.

Art

---

### Post by Cubytus on 2012-07-28
I don't understand video "in a buffer". What does that mean? I mean, video isn't recorded when there's no motion, but possible recording must start very quickly and the computer to keep up with the framerate as well as firing alert emails as fast as possible. My apartment is made in a way that possible points of break-in cannot be filmed simultaneously, and "bubble-gum" video cams typically have a narrow viewing angle, an issue I don't know how to correct properly. In fact, when setting the security system up, I always assumed a would-be thief would take as much evidence with him as he can, hence it relying heavily on permanent internet access to store a copy of pictures, or at least, send them by email. Just tripping an alarm wouldn't be of any help if the intruder has time to get away and there's no description of him. Was this assumption correct? Is it better to try to catch the thief using video evidence, or send an alarm to me and hope I would be able to explain the police that something triggered an alarm at may house and that they should have a look?

I'm not sure, either, if I do understand "bubble gum" cam correctly. Are these able to operate standalone, without a computer? If so, I already have two of them, with motion detection mode, but both are hampered with a very short battery life, so I run them as webcams instead. A spy-cam alarm clock I bought only had 2 hours of battery before dying completely, clock included, so I was looking for a way to feed it with DC while keeping the battery charged. The tricky part is, USB port on it seems to turn on only when the video camera isn't operating. Of course, it would be too dangerous to feed a battery without any kind of regulator circuit, so I'm looking for one small enough to fit inside the case.

Still, BlueIris, even not recording, takes a large chunk of CPU power to display the video feeds. That issue may not be present when recording without displaying preview, as I always minimize BlueIris' interface when starting surveillance. When recording, I set it up to use XviD compression since I think it takes less a toll on CPU than H264, and quality difference is negligible for that use. It uses more space, but the laptop has 750GB HDD, so should be ok. There's motion detection set up by software, and I often get false positives when sunlight changes too quickly outside. However, I don't like the fact BlueIris doesn't allow for any sort of cycling between cams, or record pictures on the same, larger frame.

Next modification I'll make to the cameras will be to install an IR-lighting that can run on battery if mains is shut down. It is much faster said than done. I would have to find high-power IR LEDs (3 watts each), solder suitable drivers, connect a charger that will keep a backup battery charged, and put everything in a decent enclosure so it doesn't look as a sore in my room. In fact, I'm counting on the video cameras to be non-evident for them to have enough time to capture images of a possible intruder before he leaves. Only the USB cables are still visible, as the computer. These are my present limitation: how should I get rid of them?

"Magnet wire", is it the enameled copper-colored wire used to make inductors? Can they be used in great length to replace a USB extender and still be stable enough? These extenders are typically limited to 2 metres to avoid too much signal loss.There are no like a phone cable where DSL signal runs.

How should I understand "scaling down" the system? I have the feeling it's not fail-safe enough, yet I am already finding that I spent quite a sum on something that was, until recently, useless since the neighborhood was deemed safe.

Thanks for your insight

---

### Post by SteveDee on 2012-07-28
> **goodbye-windows(tm) said:**
> ...My P4 runs cool with just a heatsink provided the processor load is kept under 15 percent....

Keep an eye on the Raspberry Pi ($35). WebCam drivers are a bit of a problem at the moment, but I expect this will be sorted out during the next few months ([http://www.raspberrypi.org/](http://www.raspberrypi.org/)).

[QUOTE=Cubytus]
...I would have to find high-power IR LEDs (3 watts each)...
[/QUOTE]

...seems like a lot of power. Most cams are very sensitive to infrared, so long as you remove the iR filter.

---

### Post by Cubytus on 2012-07-29
Please bear in mind that I intend the IR LEDs to light up the entire room, as seen from the camera. I don't necessarily expect a would-be thief to come close to the video camera.

Besides, do webcam feature an IR filter? Since every component is so small, how do I recognize what the IR filter is, in a webcam? And how do I make sure it doesn't degrade performance too much in natural light?

---

### Post by SteveDee on 2012-07-29
> **Cubytus said:**
> Please bear in mind that I intend the IR LEDs to light up the entire room....do webcam feature an IR filter? ...how do I recognize what the IR filter is...degrade performance...?

You probably need to experiment in order to assess what you need, and how good or bad the results, but here are a few comments.

Your light source just needs to cover the range of your camera (or each camera if more than one). If you have a wide-angle lens, you need a wider spread of light, but your intruder will need to get closer to the camera for you to be able to recognise him/her.

This camera ([http://www.maplin.co.uk/miniature-covert-nightvision-cctv-camera-with-audio-104962](http://www.maplin.co.uk/miniature-covert-nightvision-cctv-camera-with-audio-104962)) is an example to show that 8 small iR leds can give you a range up to 3 metres (over 9 feet) so someone moving around at that range should trigger your system, but would need to get closer for a positive id.

Does iR light degrade quality? Yes it does, that's why they usually fit filters. But I don't think this will be a worry for your security system during daytime, or with room lights switched on (I may try and generate an example picture for you, if you think that will help). Obviously video taken when the room is dark (but with iR lights) will be rendered in grey-scale. 

I supose another point is whether a night-time intruder would move around in the dark or turn the lights on. Maybe you just want to raise an alarm rather than produce video evidence.

Removing the iR filter for a given lens is not something I'd recommend for an expensive camera. If you have a cheap camera and you can find something on YouTube showing how someone else has done it, fine. The biggest problem is usually opening the camera case without wrecking it!

The filter is usually a piece of red tinted glass. In the EyeToy picture attached, its the square glass stuck to the back of the lens.

---

### Post by Cubytus on 2012-07-30
Thanks for all your detailed answers. Of course I could use an example picture with, and without IR filter fitted, showing quality difference.

 In fact, I am a bit worried to remove the IR filter as one camera seems to already see somewhat blurry at a distance. An intruder would have to pass ~2metres from the camera in any case, at its closest point. The trade-off is as such: the closer he gets to the camera, the most likely he is to get ID'ed, but the fastest the camera-computer-email chain must be to capture a clear picture before he takes away the computer (worst-case scenario: the walking path is perpendicular to the camera).

I am pretty sure a would-be intruder would use some sort of lights, but not necessarily the mains lights. To remain as stealthy as possible, maybe using a flashlight. The human eye is more sensitive to light than webcams, and, as such, when I still can see clearly enough to find the doors and use the bathroom without making a mess (!), for the camera, it's complete darkness.

The main camera is in fact very easy to open: four Philips screws hold it together, and all parts are readily accessible. I'll give it a try.

Alarms *per se* are useless IMHO. The alarms goes off, then what? The thief finds the control box, cracks it open, and cuts mains, battery, siren and phone wires, then resumes what he started. With a bit of luck I would already be alerted, but by the time I explain the police I'm calling about my apartment even if I'm not there, they may or may not catch the intruder. Major advantage if I can give them a picture right away. Neither an alarm nor videosurveillance can actually stop a thief, but the latter can at least allow to give a description. Hiding the various control boxes or recording device isn't always possible in a rented place. Plus, in this 60yr old building with no electrical upgrade, one major constraint is the power receptacle localization. I can only try to hide the boxes so much near one outlet, otherwise the extension would reveal where it is anyway. And there are no outlets near the wardrobes.

---

### Post by SteveDee on 2012-07-30
> **Cubytus said:**
> ...I could use an example picture with, and without IR filter fitted...

I can't really do a "before and after" example, but the Eyetoy image is without and the Advent image is with iR filter.

The Advent is a much better camera, but at least this gives an idea how the infrared light distorts the picture. 

I think you have a real tough problem.

---

### Post by goodbye-windows(tm) on 2012-08-06
> I don't understand video "in a buffer". What does that mean?Video signals from cameras are fed to the computer constantly. The computer always keeps the video for some predetermined period, say 30 seconds. Thus, the trigger speed can be sluggish, and you don't miss any useful video. Video older than 30 seconds without a trigger signal are discarded, usually without even being written to the harddrive.

You have the right idea about the bubble gum cams. Yes, they do operate stand alone and they do have sound activated recording. But, I think they turn off the whole camera after a certain period even if it's being powered by a car battery.

Wireless is used to link camera(s). Usually the interface that outputs to a single USB connector is proprietary. And wireless video cams aren't cheap.

Regarding the IR filters. All (most) cameras have them and they are easily spotted and removed when the camera is taken apart. The primary cause of degradation of picture quality comes if the camera is used outdoors in bright sunlight (game cameras have these issues). For indoor lighting, there isn't much degradation.

You want a system to nab the thieves, and this is admirable and I share this goal. But, a system to alert you and/or make the thieves think there is an alarm is easier and cheaper to implement. 

Twisted pair transmission line is not bad at rf frequencies. Coax is very expensive and is an unbalanced system. So, twisted pair magnet wire can be used for 20 or 30 feet long feeds. I'm not sure why it's not used more than it is. 

When my system becomes completely functional, it will include lots of fake high visibility cables and the sensors will be zero false positive  types. And, there will be a fake burgular alarm panel in order to make the thieves think they defeated the security system::>

My (functional) security system will be stealth. It's easier to do in a house than an apartment though. Houses have full basements, garages etc-lots of great places to install stealth based systems.

Really cheap narrowband  (wireless) signals can be transmitted over short distances by using ultrasonic speakers and ultrasonic receiver modules. 

Light beams can protect doorways and choke points. I actually hallowed out a piece of door trim and installed the sensor in the trim piece. For stairs, piezo sensors securely bonded to the backside of the tread provides a nearly zero false positive trigger.

I'm presently working on a microwave motion sensor module that is hidden in a book in a bookcase. The major issue is that the range is too long and is not very directional (possible for false positive alarms). However, directional antennas of low gain are easy to build for 10 GHz transceivers. 

Do you really need video?

For me, it's all about stealth and catching the thieves in the house before the cops arrive. Dead men tell no tales. Note that if I catch thieves in my house, they would be begging for the police to arrive-and they would think they had just moments to survive::> I'd really enjoy seeing them sweat and watching them pay homage to the police for saving them from me::>

As a final comment, I see handheld computers are now just a little larger than cell phones are. They have 4GB of static ram for the hard drive and can load windows or linux. All I/O is done through the digital tv connected to it except for the wireless internet connection. They sell for $60 to $80. Check out the MK802 micro computers. A friend of a friend just bought one, it runs like a champ.

Regards,

Art

---

### Post by Cubytus on 2012-08-23
An update on this topic. Thanks to everyone who gave their two cents and alternative ideas to sort this out.

I moved the cameras somewhat to get less false positives, especially when filming contre-jour. As an added benefit, the thief I'm targeting will lose one tactic advantage since he would have to get very close to the cameras to incapacitate them, hence end up being filmed anyways. My system is clearly not as advanced as yours, as I still want to keep my apartment looking as such, and not some high-tech lair.

I actually would be (half-)seriously interested in how you expect to catch and actually capture a thief in your home while you're away. It's likely that if he entered the place, he would be able to come out. An alarm system, true or fake, is not something to be afraid off. Only in movies do alarm system operate automated weapons and traps. Either you have a lot of expensive equipment inside your home, or you're just happy to know you have the best system one man can build. I know some countries and notably the USA allow their citizens to carry a gun, with restrictions. Here in Canada, it's just forbidden. It would be a really stupid move to leave it home just to find a thief wielding his new toy. Please explain (if it's not too confidential).

The MK802 surely looks nice, but I still lack an expensive piece of equipment to use it properly ;)

As your experiment with twisted-pair shows surprising performance, cabling a USB camera, should I twist data together, and power together?

 I finally got Motion installed on an LG R510, running a stock Fedora Core 17 version. I managed to get Motion configured and running (took me a few hours), but still run into some issues when I first intended to set it up as BlueIris was set up on the P4.

- When I turn on the cameras, they don't always end up in the same **/dev/videoX** spot. The X is not always linked to the cameras, and since I'm also using the integrated webcam as a supplemental camera because of its unusually high video resolution of 1280x960, thread files are not attributed to the same webcams. This is annoying since I don't require the same treshold from every camera. Another downside is the recording computer can't be hidden for now, it has to stay in plain sight until I find a way to deport the internal webcam. How can I assign the cameras to a given slot? 

- Motion only runs through *sudo*. Although a minor issue, I would like it to run as a normal user.

- I also would love Motion to interact with other sensors, sending alerts just in case the cameras can't get anything because of low light or some other reason. Is it even possible to wire sensors to a computer without any expensive interface card? Getting sensors signal + Motion MMS would eliminate all false positive.

- Does it keeps video feeds in a **buffer**? As soon as it detects movement, it's very fast in recording it, fast enough for what I want so far. I just don't know if there's a buffer or not.

- How do I make Motion **upload** through scp? From the command line, one has to open the SFTP connection first, then upload it. But as the Motion config file is stored in clear text, I can't type the SFTP password in clear text and | the resulting answer to *scp*. Same goes for FTP: although unsecured, I still wouldn't want the password to be available in clear text in the computer.

- And when should I put the command to upload the video files or snapshot photos? Even Kenneth Lavrsen's wiki pages are ambiguous: is it faster to upload a movie with on_event_end, on_event_start, on_movie_end, on_movie_start, considering Internet connection may not be available at all times?

- While I quickly realized the great potential of storing a file reference in a MySQL table, I was more interested by having an automated way to remove files older than 30 days (arbitrary value). From what I read in Kenneth's Motion manual, there's no such command. How do I do that locally? Issue would be even more critical if I switch everything to a miniature computer with limited onboard storage.
On the server, would it be possible to create a custom PHP pages to read the MySQL table and, accordingly, retrieve files and delete them as needed? Or do turnkey solutions exist?

- As an extension of the previous question: would it be feasible that Motion first uploads snapshots of any movement captured, then upload the movie when finished, then delete the snapshots so as to leave the movie only?

-I still have yet to find an external application that would be able to **send me a MMS** with a snapshot attached to it. Does that exist in Linux, using only an Internet connection? I read that Mutt can be operated from the command line, and I actually used it, rarely, long ago at the MNI where it was the standard email client.


_On Fedora itself:_
- can't get SSH server running, so I have to manually start the recording from the command line, and shut the recording from the Web interface. That's awkward.
- calling the computer through the web browser using its Bonjour name doesn't give any answer. Only numeric IP does.

---

### Post by matt_symes on 2012-08-23
Hi

Interesting thread.

> When I turn on the cameras, they don't always end up in the same **/dev/videoX**  spot. The X is not always linked to the cameras, and since I'm also  using the integrated webcam as a supplemental camera because of its  unusually high video resolution of 1280x960, thread files are not  attributed to the same webcams. This is annoying since I don't require  the same treshold from every camera. Another downside is the recording  computer can't be hidden for now, it has to stay in plain sight until I  find a way to deport the internal webcam. How can I assign the cameras  to a given slot?To do this, investigate creating a UDEV rule for the devices.

> - Motion only runs through *sudo*. Although a minor issue, I would like it to run as a normal user.You are interested in removing the sudo password or removing sudo altogether ?

For the first option, one way is to add the program is a trusted program under sudoers. Set it so that only you can run the program without entering a sudo password.

For the second option, see if adding yourself as a member of the group that owns /dev/videoX helps (maybe video) or set up ACL on the device file and add yourself.

> 
- While I quickly realized the great potential of storing a file  reference in a MySQL table, I was more interested by having an automated  way to remove files older than 30 days (arbitrary value). From what I  read in Kenneth's Motion manual, there's no such command. How do I do  that locally? Issue would be even more critical if I switch everything  to a miniature computer with limited onboard storage.Is the video stored as a regular file ? if so, maybe a Cron job run once a day using a variation of 

```
find . +a(m)time -delete {} \;
```?

I have never used motion so these suggestions are nothing more than that.. suggestions :)

Kind regards

---

### Post by SteveDee on 2012-08-23
> **Cubytus said:**
> I know some countries and notably the USA allow their citizens to carry a gun, with restrictions. Here in Canada, it's just forbidden....

Yeah, same here. But we are allowed to keep a 6ft Boa Constrictor in a glass tank...also put the computer in to keep it warm!
> 
...Motion only runs through *sudo*. Although a minor issue, I would like it to run as a normal user.

If you haven't done this already, you need to create a hidden folder in your user home like this: /home/Cubytus/.motion and copy your motion.conf files here. Then make sure you have read/write permissions. Motion will look here first when you run as user Cubytus.
> 
...is it even possible to wire sensors to a computer without any expensive interface card?...
Well the Velleman K8055 is about £30 here. And of course the Raspberry Pi has a built in GPIO (but there are still USB camera issues to be resolved).
> 
...would it be feasible that Motion first uploads snapshots of any movement captured, then upload the movie when finished, then delete the snapshots so as to leave the movie only?

I don't get the gist of your question, but I can say that you don't need to save jpeg stills if you only want video. Motion stitches together the frames as they arrive and converts to whatever video format you have requested.

---

### Post by Cubytus on 2012-08-26
I'll look into UDEV rules later, as I now got a more serious issue with Motion. Also, let's forget about the RaspberryPi for now, as it doesn't support webcams properly yet.

First, it seems that, even when running off the script and no error is detected on launch, config line
```
on_movie_end wput %f ftp://username:mypassword@myftpserver/vid/motion 
```
just silently fails. It means that no movie is uploaded, although they're correctly recorded. Same goes for the snapshots that are supposed to be uploaded through
```
on_picture_save wput %f ftp://username:mypassword@myftpserver/vid/motion 
```
Weirdly, same command typed on Mac also fails:
```
Connecting to xxx.yyy.zzz.92:21... connecté! 
Logging in as *username* ... Erreur: Login-Sequence failed (Login authentication failed)
Skipping all files from this account...
FINI --02:15:27--
La transmission du fichier 1 a échoué

```

It means that Motion isn't being useful so far.

I want video since this it's smoother to use than a bunch of pics. However, severe upload bandwidth constraint still  favor uploading small files first, and bigger videos later. Can Motion be configured to give upload priority to small files (yes **matt_symes**, Motion generates usable pictures and videos, depending on config). Of course I there is no need to have 15 frames captured each second as motion-triggered snapshots; I suspect not having restrained the capture rate is responsible for the sluggish computer response time whenever Motion is running.

Also.. Since bandwidth is not guaranteed, is Motion able to automatically resume uploading files? And perhaps move the successfully uploaded to some other folder? Means, does it maintain an internal queue of what files were uploaded, and which ones are waiting?

Other issue that may be Fedora-related: when Motion runs, the screensaver is deactivated. Although I doubt the targeted thief would take the pain to stop motion instead of simply taking away the computer, it is still weird. But since Motion presently only runs under sudo, it means it cannot be killed if *htop* of System Monitor isn't ran through sudo.

---

### Post by Cubytus on 2012-09-10
Ok, solved the issue... The special characters in the password has to be escaped (Thanks to Q-X's team for pointing out double-quotes ("") didn't work!).



Now, I have a potentially more serious issue: when Motion runs for about 24 hours, it takes so much RAM that it crashes, defeating the idea of unattended surveillance. It starts up nicely at about 200MB, then eats all the RAM available up to 4GB, then continues on by eating the swap. When there's no swap left, it crashes. The process takes a few hours, but is very serious.

In the meantime, the router reports more than 8000 simultaneous connections to the net, that probably slows down the modem to a crawl and prevents updated snapshots to be sent in a timely manner to the FTP server. It doesn't seem to be possible to limit the amount of simultaneous connections from *wput* or *Motion* itself.

How to know what exactly is happening? Memory leak + excessive connection use?

---

