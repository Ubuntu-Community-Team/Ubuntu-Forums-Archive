---
title: "Live CD produces corrupted screen display"
date: 2011-02-09
forum: Mythbuntu
---

### Post by nhtrader on 2011-02-09
Hardware
Laptop is ASUS G60JX
CPU: Intel i5 2.27Ghz
RAM: 4 Gb
Nvidia Geforce GTS360M with 1Gb VRAM

I created two CDs:
Mythbuntu 10.10 (32bit)
Mythbuntu 10.10 (64bit)

Both CDs when inserted into Desktop work fine. Confirmed CDs not corrupted. 

But when I insert them into Laptop, the screen gets corrupted and I have to press the power button to shut it down. This happens with both CDs.

I see the initial Mythbuntu logo and then see the smaller logo with the dots. After that it goes dark for a while and then produces a corrupt screen.

Any ideas?

---

### Post by heyho on 2011-02-09
I'm no expert in this area, but maybe try some of the different boot options - ie "nomodeset"?

---

### Post by nhtrader on 2011-02-09
> **heyho said:**
> I'm no expert in this area, but maybe try some of the different boot options - ie "nomodeset"?

How does that work?

All I'm doing is turning on computer; press ESC to enter boot menu; select CD-ROM; go.

I don't see how I could change anything. I'm using the LiveCD to boot directly into Mythbuntu/MythTV Frontend.

---

### Post by nickrout on 2011-02-09
when the cd boots it gives you a prompt and asks if you want to boot.

---

### Post by nhtrader on 2011-02-10
> **nickrout said:**
> when the cd boots it gives you a prompt and asks if you want to boot.

My LiveCD works using a older laptop but not with this newer laptop.

In both laptops, the same prompts appear.

1.Turn on computer & I must press ESC quickly to enter the boot menu and make a selection
     (note these laptops are not dual boot machines where I could access GRUB. These are strictly Windows PCs)
2. I enter the boot menu prompt and select the CD-ROM
3. The next prompt I would see is the Try or Install Mythbuntu prompt.
       in the older laptop I see this prompt and make the selection Try Mythbuntu and the LiveCD continues to completion.
       with the newer laptop I get a corrupted screen and must shut it off - LiveCD use fails.

In this chain of events I don't see any other prompts. I don't see any other places where I could input a command or change an environment variable or activate an option. But note that this is off-point from the main problem of the corrupt screen. I'm just trying to learn how to implement "heyho's" suggestion "nomodeset"

Lastly, here's a footnote. While the older laptop loads Mythbuntu fine, it still fails as a FE b/c the current LiveCD available (v0.23) doesn't mesh with a v.024 BE I get a mismatched DBSchemaver error (which I have posted in another thread)

But to be clear, both laptops don't work with my operational BE. One, gives me a corrupt screen and the other can't connect. So much for the upgrading and using a LiveCD to access content remotely. (so now I've explored two methods to access content remotely: AV renderer/UPnP and LiveCD. both aren't working properly yet.)

Had I left the desktop alone (hadn't upgraded), I probably could have at least one laptop using MythTV's FE remotely. As for the other, the problem remains why the LiveCD produces a corrupt display. And to top it off, there isn't a LiveCD with the latest version of MythTV (0v.24) yet. So I'm trying to learn how to do this too - create one.

---

### Post by nickrout on 2011-02-10
Don't forget that there are precompiled mythtv binaries for windows available.

---

### Post by nhtrader on 2011-02-10
> **nickrout said:**
> Don't forget that there are precompiled mythtv binaries for windows available.



I'm glad you mentioned that.

Long story short. That didn't work out either. Here's what I learned about the precompiled windows binaries.

1. First I started with a win7 laptop and installed the precompiled mythtv binary for windows (PMB4W). My BE is installed on a separate PC(desktop) using v0.23-rev26437 .  The PMB4W installed on the laptop was a FE only install of v0.23-fixes-25174 . This produced a network error.

When I ran the "mythtv for windows on Win7 laptop, I got this error...
"The server uses network protocol version 23056, but this client only understands version 56. Make sure you are running compatible versions of the backend and frontend."

After I pressed <enter> the prompt disappears and so does MythTV for Windows.


So the next step was to use the next version, as was the advice of the member who created these binaries. So I uninstalled the v0.23-fixes-25174 and then installed v0.23.1-fixes


This version didn't produce the network error and loaded the frontend just fine. But the frontend was not fully functional on my win7 laptop.


1. Surprisingly I was able to watch Live TV. I could watch SD and HD programming perfectly and change programs without incident. However, pressing ESC to exit fails to work as expected. The last image of the program lingers on screen and I can't back to the menu.

2. Could not enter "Utilities/Setup|Setup". It doesn't do anything. It doesn't hang b/c I can still use the Left/Right arrows to select the other menu item "Edit Keys". I don't know why I can't use this Setup Section.

3. Selecting "Media Library" causes the Frontend to crash... and windows displays the following message: "MythTV Frontend.exe has stopped working" Select Close Program.



The next suggestion was for me to delete the entire TERRA theme.

This made an improvement. But problems still existed. Here they are...

1. Accessing all menus is now possible

2. Watching Recordings is now possible, but exiting a program still results in a frozen view of the last image displayed and loss of functionality. Using ALT+TAB doesn't work. Must use CTRL+ALT+DEL to enter Task Manager to get back to main menu. The MythTV's tracer reads...
TV: Attempting to change from WatchingLiveTV to None
TV: Changing from WatchingLiveTV to None


3. I tried to use MythMovies and I was able to enter zip code plus other info and press button "Finish".
Then this error message appeared with an OK button...
"Failed to process the grabber data"

However in the background of this prompt, I could see the following...
MythMovies Data Grabber Failed
C:/Program failed: does not exist
Check MythMovies Settings


4. Use of FastForward and Rewind is sporadic. Sometimes works as expected, other times you can hear the shift in the audio track but the video remains frozen on the last image displayed b4 keys were pressed.

When this errant behavior occurred, I noticed MythTV's tracer reporting this...

Couldn't load deinterlace filter
Video timing method:USleep with busy wait
Couldn't load deinterlace filter
Failed to enable deinterlacing
MythContext: Connecting to backend server: 192.168.1.12
Using protocol version 23056





Then I upgraded to MythTV v0.24 on the Desktop which runs my BE.

Then I uninstalled v0.23.1 from the Win7 Laptop and installed v0.24-fixes-rev145

This version also has problems with default theme and changing themes improved responses.
But with this version I can hear the audio track but can't see the video. All I see is a black screen with "Please Wait...."
It doesn't matter if I'm watching LiveTV or watching a recording. I still see "please wait". But I hear the sound track.

So at this point, I gave up and moved on to LiveCD. 



So you see I've been busy trying all of the remote access options and none are working for me that involve MythTV.

I can also add that I've tried xbmc. Surprising this works quite well for recordings, but there's the rub. No LiveTV; no commercial skipping; and other things that MythTV does so well when it works.


But again, this summary of my experience with MythTV's remote access is off-point from the essential question asked in this thread. And hopefully you can appreciate the how methodical I've tried to be in exploring all available options and hopefully understand my frustration. 

I remain hopeful in finding solutions to get all of my PCs to access mythtv's recorded content.

---

### Post by nickrout on 2011-02-10
OK now that you have upgraded your backend to 0.24, try the 0.24 windows binaries, seems to work ok for me on win7, although a vista machine wouldn't play ball. I haven't tested extensively.

Second option: dual boot. You won't need a big chunk out of your laptop's hard drive, as you won't usually be storing any media locally. I can't remember how much space a bare mythbuntu install takes, but you will also need some space in /var/cache/apt/archives to download upgrades to - although you can clear that directory out after you have done each upgrade cycle to keep it lean.

Then there are the other options alluded to in this or another thread - produce a bootable flash drive and update it to latest versions.

---

### Post by nhtrader on 2011-02-10
> **nickrout said:**
> OK now that you have upgraded your backend to 0.24, try the 0.24 windows binaries, seems to work ok for me on win7, although a vista machine wouldn't play ball. I haven't tested extensively.



I mentioned that I had installed the 0.24 windows binary (v0.24-fixes-rev145  see post #7). I've tried this already. This version was the worst yet. I couldn't view anything but a black screen with "Please Wait..." Although I could hear the soundtrack.

---

### Post by nickrout on 2011-02-10
> **nhtrader said:**
> I mentioned that I had installed the 0.24 windows binary (v0.24-fixes-rev145  see post #7). I've tried this already. This version was the worst yet. I couldn't view anything but a black screen with "Please Wait..." Although I could hear the soundtrack.

sorry I missed that part of your post...

Works for me, but it could be a difference in our windows hardware that explains it. What do the logs say?

---

