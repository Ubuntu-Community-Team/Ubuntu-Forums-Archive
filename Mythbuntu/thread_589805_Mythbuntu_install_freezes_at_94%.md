---
title: "Mythbuntu install freezes at 94%"
date: 2007-10-24
forum: Mythbuntu
---

### Post by snwbrder0721 on 2007-10-24
So I just used the gparted live cd to partition my drive, now I go to install mythbuntu 7.10 and everything seems great... until my system locks up at 94% installed. I remember reading that sometimes everything is installed at this point so I try to boot up, not luck just lots of errors. I'm going to reformat and partition again then try the install again. In the meantime, is there anyone who has some ideas as to why I'm getting this problem or is it just random hardware glitches? Thanks.

My system: dell 733mhz P3, 386 mb ram, nvidia geforce fx 5500, 20gb WD HD, PVR-350 tv card.

---

### Post by superm1 on 2007-10-24
Are you using the final ISO?  There were issues with previous ISOs and this area.  If you're not, download the final ISO.  If you are, can you check /var/log/syslog on the running (installing) system?  Any indications of what is going wrong?  Post it here if you aren't too sure.  Also, any odd options that you chose or anything?

---

### Post by snwbrder0721 on 2007-10-24
I'm using the 7.10 i386 ISO that was just released monday. Here's some screenshots of my problems attached below. I labeled each image with a description of the problem. Let me know if that helps and thanks again for your replies to my issues on here.

---

### Post by davemorris on 2007-10-24
Redo the installation whilst tailing the log with

 ```
tail -f /var/log/syslog  
```

the when it hangs it will tell you what it's been doing.

---

### Post by snwbrder0721 on 2007-10-24
Sorry, one of my images didn't upload, it was when I started in "recovery mode" it failed to load the hardware drivers. During the install the only non-standard options I choose were to use the proprietary nvidia drivers (nvida_new) for my graphics card, and to enable the hauppauge tv card remote for my tv card.

---

### Post by snwbrder0721 on 2007-10-24
@davemorris

Can I run that code in from the mythbuntu live CD? I'm doing a clean install so I don't have a current OS to run it from otherwise. Thanks.

---

### Post by snwbrder0721 on 2007-10-24
Ok, so I tried the install again with the advice above from davemorris.
I've attached the screenshots with various warnings I saw during install and the final output I got before it froze (at 93%-configuring hardware). The only thing I did different this time from last was to use the open source video drivers instead of the nvidia ones. Obviously, not a help. 

The first several shots are some warnings I saw, not sure if they are relevant or not (apt API not yet stable, and later, cannot read table of mounted file systems).
The final error screen is broken into a left and right side so it could all be readable. the last things seems to be
 ```
ubuntu ubiquity: update-initramfs: generating /boot/initrd.img-2.6.22-14-generic
```

---

### Post by snwbrder0721 on 2007-10-24
Judging from the previous install error on loading hardware and the fact that the installs are freezing around 93-94% which seems to be the hardware configuration section, could there be something with my hardware that is causing this problem? And if so what can I do to make this work? (my hardware specs are in my earlier posts) Thanks!

---

### Post by superm1 on 2007-10-24
Those are all normal messages according to your screenshots.  

How long did you let it sit there?  Steps 93-96 take a long time. 

Can you post an entire /var/log/syslog here?  You can open up a terminal during the live session to see it in its entirety rather than having so switch over to a VT like you did for the camera shots.

---

### Post by rjs82vette on 2007-10-24
I was stuck 83 percent for 2 hours before it decided to continue on with the install.

I just let it set, but I was installing it in virtualbox so I am used to certain OS's taking a while to install.

Sun Solaris took about 8 hours to finish up.

---

### Post by superm1 on 2007-10-24
> **rjs82vette said:**
> I was stuck 83 percent for 2 hours before it decided to continue on with the install.

I just let it set, but I was installing it in virtualbox so I am used to certain OS's taking a while to install.

Sun Solaris took about 8 hours to finish up.
Sounds like your PC was pretty starved for CPU.  I can do an install in virtual box in about 15 minutes.

---

### Post by snwbrder0721 on 2007-10-24
@superm1
Could you give me more detailed instructions on opening the syslog? I'm still pretty new to linux (1 week of use, but I've learned a lot from the problems I've had like this one). Before I ran the last install I ran the following code, as davemorris had instructed earlier: tail -f /var/log/syslog

I let it sit there @ 93% for about 20 minutes. I'll try it again tonight and let it sit while I watch the World Series (go Rocks!)

Thanks for the help so far, I'll report back what happens next.

---

### Post by snwbrder0721 on 2007-10-24
@rjs82vette
What's your system specs? I'm curious if they're close to mine (see below) so maybe I can judge my expected wait time based on your experience. Did your system actually lock up at 83%??? My mouse and keyboard become totally frozen at 93%. Thanks.

---

### Post by superm1 on 2007-10-24
Ah okay.  Well easiest way to look at that log is to probably install an editor in the live env like leafpad, mousepad, gedit or geany.

Go ahead and start it like this:

```
gedit /var/log/syslog
```

Once you do that, you will get the whole log opened up.  You can select the whole thing and copy it to a clipboard.  Open up firefox in the live env and then paste it into your post :)

---

### Post by snwbrder0721 on 2007-10-25
Tried install again, this time let it sit for 2 hours. Still froze at 93% ("configuring hardware"). My next thought, which I'll try tomorrow, is to take out the TV tuner card and use the open source video driver. Not sure if that will matter, but anythings worth a try at this point.

@superm1
I'll also try logging the syslog with gedit like you mentioned and see if that turns up any hints

I'm wondering if maybe it'd be better if I installed xubuntu 7.10 and then the mythtv package and tried to fight the mysql problem I had before (I couldn't connect to mysql database / didn't know what the hell I was doing at all).

Another possibility, I could install mythbuntu on the HD I'm currently using via my main HP windows machine and the live CD, except I have yet to get a live CD to even load on my Windows machine (freezes while loading in ubuntu, xubuntu, mythbuntu, tried multiple times). Is there a alternate (text) install version of mythbuntu available?

Now that I'm up to about 20 some hours on this linux tivo project I'm thinking that buying a real tivo might not have been such a bad idea. (but I'm not giving up quite yet).

Again, thanks in advance for any help anyone can provide.

---

### Post by snwbrder0721 on 2007-10-25
Ok, so I just tried the install again, this time with the hauppauge pvr-350 card removed. I didn't configure a remote, and used open source graphics drivers. The install got farther (95% then back to 94%) but still locked up at:
 ```
ldconfig deferred processing now taking place
```

See the screen shot below for more info. Anyone know what this might indicate?

Since it says "deferred processing" I'm gonna let it sit for a while (about 10 minutes have elapsed so far) and see what sort of magic happens, but I'm not holding my breath.

 I'll try the install again with the gedit syslog thing superm1 suggested for more info, but it will have to wait until a bit later today.

---

### Post by snwbrder0721 on 2007-10-25
@superm1
Quick thought, if I'm looking at syslog through gedit and the mahcine is totally froze, they'll be no way for me to get to the clipboard to get the syslog text right? (I've been making these posts from my windows machine, switching my monitor back and forth between it and my wannabe mythbuntu box)

Would the output be any different?

I wouldn't mind transcribing what is on the screen if you thought it might bring us closer to a resolution.

---

### Post by snwbrder0721 on 2007-10-25
Ok, so I waited 45 minutes and still nothing happened with the "ldconfig processing". So I restarted and tried to boot off the hard drive. Things started loading, then when it go to "hardware drivers... failed" then a bunch of stuff flashed by, something about unable to communicate with hardware due to "dbus" and then the textual login prompt (see one of my first posts for a screenshot, it asks for login, then password, then has a whole sting of errors, then nothing). So another failed install in the end. 

Does this give anyone any further clues to my mystery? Since it seems to be a hardware related hangup is there anything I might have that would cause this?

I won't have time to retry thing until this evening, but I'll post my results, good or bad and see what we can come up with. 

Thanks again everyone for your support on this.

---

### Post by snwbrder0721 on 2007-10-26
More of the same when I tried installing again last night with the TV card out. I even tried going through and choosing all kinds of different settings in the install (not necessarily the best choices, but just looking to get something different), no change in the end result.

This has got to be one of those so obvious it's simple kind of things or a really rediculously complex problem. Either way I'm lost and too unfamiliar to linux to figure anything else out.

If anyone has any ideas let me know. Otherwise it's back to xubuntu and then the mythtv package, which probably means you'll see some posts about my mysql problem again.

---

### Post by rjs82vette on 2007-10-26
Mmmm not starved for CPU power.... newest quad core system here...... I am not sure why it took so long just that it did..... I also had issues with Solaris but just about everything else install just fine....


I have running in VBox......

all windows versions from dos to vista

kubuntu
ubuntu
mythbuntu
PClinuOS
Vixta
Linux XP
Fedora 7
OS2 Warp 4.52
clark connect

working on Mac OSX

---

### Post by Fragadelic on 2008-09-12
I know this is an old post but I know whats going on.  I am the author of the remastersys script and I've narrowed this issue down to the fact that the reconfiguring of the popularity-contest package is causing this.  I'm still looking for a solution myself.

---

### Post by superm1 on 2008-09-12
> **Fragadelic said:**
> I know this is an old post but I know whats going on.  I am the author of the remastersys script and I've narrowed this issue down to the fact that the reconfiguring of the popularity-contest package is causing this.  I'm still looking for a solution myself.
While this may be the case of the GTK frontend of Ubiquity, it's a little bit different in mythbuntu's frontend.

Between 93-95 percent, a lot of stuff happens.

This is when a lot of the "extras" for Mythbuntu get installed.  You can browse through some ubiquity code to see the difference for Mythbuntu in 93-95 percent.

Mythbuntu:
```
            self.db.progress('SET', 93)
            self.db.progress('REGION', 93, 95)
            self.db.progress('INFO', 'ubiquity/install/installing')
            self.add_drivers_services()
            self.enable_cdrom()
            self.install_extras()

```
GTK Frontend
```
            self.db.progress('SET', 93)
            self.db.progress('REGION', 93, 94)
            self.db.progress('INFO', 'ubiquity/install/bootloader')
            self.configure_bootloader()

            self.db.progress('SET', 94)
            self.db.progress('REGION', 94, 95)
            self.db.progress('INFO', 'ubiquity/install/installing')
            self.install_extras()
```

---

