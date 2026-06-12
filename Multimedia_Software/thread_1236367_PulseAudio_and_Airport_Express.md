---
title: "PulseAudio and Airport Express"
date: 2009-08-10
forum: Multimedia Software
---

### Post by Runei on 2009-08-10
Hello. This is the first time I've installed Ubuntu 9.04, or any Linux for that matter, so Im waaaaaaay newb in this.

Before I had Vista, and enjoyed the sweet music from my laptop streaming through my Airport Express to my stereo.
I would very much like to do that again.

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Airport_Express](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Airport_Express)

On that website I found some guide explaining how to stream music to the Airport Express, I think, but I ran into some problems.

First of all - This is all still quite confusing to me, but I'm learning.

When I choose Applications --> Sound & Video --> PulseAudio Device Chooser
The only "program" that opens is the little icon in my top right of the desktop (It says PulseAudio applet). Left-clicking it brings down a drop-down menu, where you can choose 
Default Server, 
Default Sink, 
Default Source, 
Manager, 
Volume Control,
Volume Meter /Recording), 
Volume Meter (Playback), 
Configure Local Sound Server, 
Preferences, and 
Quit.

Non of these get my to a window where I can choose Network Access, as it says on the website I posted.

Instead I have to go to System --> Preferences --> PulseAudio Preferences
Then I get a window with 3 tabs. Network Access , Multicast/RTP and Simultaneous Output.

In Network Access I see 4 checkboxes. 
Enable Network Access to local sound devices (This one I can check or uncheck as I choose)
Allow other machines on the LAN to discover local sound devices (This I cannot check, no matter if I check or uncheck "Enable Network Access....")
Don't Require Authentication (This I can check if "Enable Network..." is checked)
Make discoverable network sound devices available locally (this I cannot check)

The last one is one of the two checkboxes it says I should check on the website, and I cannot. The other checkbox it says I should check (The one about airtunes) is not even there.


Can a clever, good-hearted soul please help? Maybe take me through step by step, because I really suck at this right now I guess...

---

### Post by efgevh on 2009-08-10
> 

Non of these get my to a window where I can choose Network Access, as it says on the website I posted.



what about the "configure local sound server" entry ?


> 
In Network Access I see 4 checkboxes. 
Enable Network Access to local sound devices (This one I can check or uncheck as I choose)
Allow other machines on the LAN to discover local sound devices (This I cannot check, no matter if I check or uncheck "Enable Network Access....")
Don't Require Authentication (This I can check if "Enable Network..." is checked)
Make discoverable network sound devices available locally (this I cannot check)


Ok,  did you install all the required packages, what about paprefs which takes care of networking?

---

### Post by Runei on 2009-08-11
Hey thanks for the reply!

My bad about "Configure Local Sound Server". That brings me to the screen with the three tabs one of them being "Network Access".

I think I installed all the packages... How can I tell if I didn't, and what commands should I use in the terminal?

cheers

---

### Post by efgevh on 2009-08-11
You can see from the 
system --> preferences --> synaptic package manager
if a package is installed or not

there's a detailed thread here on sound in jaunty:

[URL="http://ubuntuforums.org/showthread.php?t=1130384"]http:
//ubuntuforums.org/showthread.php?t=1130384[/URL]

based on your problem perhaps you should check the following

"In System/Adminstration/Users and Groups check that your users and root are members of the following groups. (This is supposed to be taken care of by Policykit and hal but users have reported messages in their logs relating to lack of permission for pulse to gain rt priority so.....)
pulse
pulse-access
pulse-rt

Reboot "

---

### Post by Runei on 2009-08-12
Thanks again.

It seems the update manager on Jaunty automatically updated PulseAudio and also installed paprefs. Nice!

Now I could find the checkboxes I needed.

My user is a member of those groups.

Now I just need to detect my Airport Express.

Right now it doesn't seem to detect it...

Any ideas?

thanks,

---

### Post by efgevh on 2009-08-13
So have you installed 
Pulse Audio 0.9.15
Pulse Audio Volume Control 0.98
pulseaudio-module-raop

jaunty default is pulseaudio 0.9.14

---

### Post by Runei on 2009-08-13
Yep it's all there. I only need to find my Airport Express now.

When I had vista, I first had a problem with the Airport, that I couldn't be connected to my internet router and the airport express at the same time. 
I fixed this problem by making the Airport Express part of the router network. This way I could be online and connected to the Airport Express at the same time.

Does Pulse Audio cut the internet connection if it connects to the Airport Express?
Could it be that PulseAudio cannot find the Airport Express, because the Airport Express is still sitting as a part of the router network? In that case - Whats my next step?

Would reseting the Airport Express help? Knowing that I cannot use the Airport Express managing program with ubuntu...

---

### Post by Runei on 2009-08-13
UPDATE:

Something happend.

I went to check the Volume Control program and what do I see? Suddenly in the Output devices (or something... mine is in danish so I don't know what it is in english) Well - I see my airport express called "Stuen". 

There were 2 devices. An HDA Intel and "Stuen". Both of them had a red cross infront of the loudspeaker icon, and the HDA Intel was set as default. First I try to press the loudspeaker icon with "Stuen", but and error says something about connection failed, and the program closes. 

I try it once more, this time setting "Stuen" as default. Clicking the icon still generated the connection failed error and the program closes. When I open it once more the "Stuen" is gone...

Hm...

---

### Post by Runei on 2009-08-14
Okay. Now I can find my Airport Express unit.

Next trouble is how to get it to work.

If I try tampering with the volume control for the Airport Express output signal I get and error that says:

pa_context_set_sink_volume_by_index() failed: Bad state

Anyone knows what it means?

---

### Post by ballardhd on 2009-08-14
I get a similiar message after I make my Apple TV my default sink in the volume control UI.  Once I try and move the volume control, pulseaudio crashes and I get the error:

> Connection Failed.  Connection Terminated.

Has anyone had any success in playing any actual music after connecting to their Airport Express / AppleTV device?  I running Jaunty and Pulseaudio 0.9.15...

---

### Post by PaddyF-disabled on 2009-09-15
I'm having similar problems. I'm totally new to Linux. I installed Karmic, which came with all the latest pulseaudio modules. I'm connected to the internet via the Airport Express, and Airtunes is enabled on the Airport Express itself.

In pulseaudio, I checked the "Airtunes" checkbox in the "Configure" dialog, but I don't see the Airport listed anywhere (should it be in the "default sink" list?). What else in the "Configure" dialog should be checked and unchecked?

Also, although module-raop is installed (it says so in the package manager), I didn't see it mentioned in default.pa. I added a "load-module" line for module-raop to default.pa and restarted, but it didn't work and also broke the audio from Firefox.

Any ideas?

---

### Post by klap-in on 2010-05-13
When all the needed stuff is installed (paprefs pavucontrol pulseaudio-module-raop pulseaudio-module-zeroconf). Here helps the following to (re)enable the Airport:

In Pulseaudio preferences window: Check off the airtunes option, close window and open window again and check on the option: 'Make discoverable Apple Airtunes sound devices available locally' and close window again. Now the Airport is discovered again on my machine.

---

