---
title: "Experiences with 8.10, Logitech Vision Pro &amp; Skype"
date: 2008-11-22
forum: Multimedia Software
---

### Post by forkandles on 2008-11-22
As most of us who use Linux know, Windows webcams can be a complete nightmare in Linux and other applications like Skype.
I had read a review on ASE Labs which stated that the Logitech Vision Pro webcam worked perfectly in Linux (well, Ubuntu at least), as well as with Mac and Windows.
[http://www.aselabs.com/articles.php?id=268&asesessid=aa58de41ab3433ec951eba636a7e4a3c5b546fe4](http://www.aselabs.com/articles.php?id=268&asesessid=aa58de41ab3433ec951eba636a7e4a3c5b546fe4)

As a result of this review I purchased a Logitech Vision Pro.
However, I still could not get it to work with my previous Linux OS.

I then decided to try Ubuntu 8.10 with the 2.6.27-7 kernel, which crucially contains improved support for webcams.
The webcam was recognised immediately by 8.10 and the test video worked. It then took me a while to get the sound working. Many thanks to joris1977 and psyke83 for their articles.

To help others in a similar predicament, this is what I did.

METHOD:

Go to the link below:  (I added numbers 1,3,4,7,9)

[http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

I also added, via Synaptic, the small but powerful text editor, vim. Alternatively use gedit etc. Here is a brief tutorial on vim:
[http://tips.webdesign10.com/another-vim-tutorial](http://tips.webdesign10.com/another-vim-tutorial)

Go to the following link and scroll down to “Packages”. Doing searches for alsa and pulseaudio will find most of them. Use Synaptic to install them. 

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Now you need to add the text specified below to the file
       /home/myusername/.asoundrc
(where “myusername” is, for example, jimmy)

Open the terminal and type   vim /home/jimmy/.asoundrc

You will be asked for the password (e.g. laptop). Type    laptop    and press the
Enter/Return key.

Press “i” which takes you into Insert mode. Using the Down Arrow key place the cursor at the start of the first empty line. The previous line should end with .........asoundconf>
Add the following text EXACTLY as it is displayed here (copy and paste this)

pcm.!default { 
 type pulse 
 } 
ctl.!default { 
 type pulse 
 } 
pcm.pulse { 
 type pulse 
 } 
ctl.pulse { 
 type pulse 
 }

Now press the Esc key, which returns you to Command mode and type
  :wq       

To check that your file amendment has worked, click on:
Places > Home Folder > View > Show Hidden Files > Double click on   .asoundrc
Exit the terminal.

Take a break. 
Then go into your Skype account. If you don't have one, then press Alt + F2 , type   skype     and press Run. Answer all the questions to set up your account.

**Make sure the webcam is plugged in DIRECTLY to one of your pc's USB ports and  NOT via a USB hub!**

In the bottom left hand corner of the Skype box there is a small blue Skype logo (Main Menu) with a black down arrow. Click on the icon/arrow, select Options > Video Devices.
All being well, under “Select Webcam” you should see the Logitech and Vision Pro codes:      UVC Camera (046d:09a6) (/dev/video0)
plus a white Test button on a black background.
Make sure the Enable and Auto boxes are ticked (checked).
Under Receive, select “anybody”. Under Show, select “only people I have allowed”.
You may need to exit Skype and reboot the pc. 

To fully exit Skype right click on the green icon in the top toolbar and select Quit. 
If you have left an existing Skype account open unknowingly, when you try to reopen Skype it will probably prevent you from logging in to your account.

Log in to your Skype account again and press the Test button to see if your video is working.

Your SOUND SETTINGS now need to be set correctly for PulseAudio. 
This will vary from one person's pc and circumstances to another so you will probably have to fiddle about with the settings. 

To complicate matters, there are FIVE different locations in Ubuntu and Skype for setting sound preferences. Each location contains several options. I have not bothered to calculate the total number of possible permutations, but it is a lot.

1) In Skype Main Menu > Options > Sound Devices.
Set both Sound OUT and Ringing to pulse.
Set Sound IN to HDA ATI SB (hw:SB,0)                          (This is mine)

2)Applications > Sound & Video > PulseAudio Device Chooser (applet in the top toolbar). The PulseAudio Volume Meter Recording should respond to your vocal input. If it does then PulseAudio is working. You can visit this link and look for joris1977's very helpful post. 

        [http://ubuntuforums.org/showthread.php?t=967362](http://ubuntuforums.org/showthread.php?t=967362)

3) System > Preferences > Default Sound Card      (Mine is SB)

4) System > Preferences > Sound. Under Devices, set the first 4 to PulseAudio Sound 
Server.
Set the Mixer to Capture:ALSA PCM on hw:1  etc       (Should start with ALSA)

**As a general point, just make sure that no sound setting is “greyed out” and that all sound sliders are set to HIGH and all mutes are OFF.**

5)Double click on Speaker Icons in the top toolbar and click on Preferences. My device is HDA ATI SB (Alsa Mixer). Choose which items you wish to have displayed and adjust their controls.

**Please note that these 5 settings are in no particular order**.

After you have played about with the umpteen sound settings, you should be in a position to make a test sound in Skype. 
Double click on Skype Test Call, record your message and keep your fingers crossed that it is played back.
If your message is replayed then your sound settings are correct and you can proceed to make Skype sound and video calls with your Logitech Vision Pro webcam.

You may do better with a separate microphone or headset. Borrow them first!

If you do not have immediate success then search these forums (Multimedia & Video) and just keep altering settings, by trial and error, until they are correct for your particular situation. 

I suggest that you print these instructions before you start and make copious notes of initial and altered settings as you go along, one step at a time. Try not to change too many settings at once otherwise it can all descend into chaos.

By the way, the Logitech Vision Pro is an excellent webcam and I can thoroughly recommend it.

---

### Post by DRHansen on 2008-12-11
Just in case you missed it above (as I did the first dozen times I read it):

[INDENT]**[COLOR="Red"]**Make sure the webcam is plugged in [COLOR="Black"][SIZE="3"]_DIRECTLY_[/SIZE][/COLOR] to one of your pc's USB ports and NOT via a USB hub!**[/COLOR]**[/INDENT]

That bit of advice seems to apply to other webcams (Logitech QuickCam 3000 Pro, Creative Webcam III) as well!  An extension USB cable works, but not a hub (powered or otherwise).

Thanks forkandles!

---

### Post by Nausser on 2008-12-23
I actually have wonderful luck plugging my quickcam fusion into a powered usb hub. Just wanted people to know there may be exceptions.

---

### Post by zob on 2009-05-16
I just bought this one because it needed no drivers. I tried it on windows and Linux (ubuntu 9.04). Works out of the box on both. It works for skype and recording with with VLC, with cheese...

So, no technical problems. And on windows XP the recording quality is great, actually it's astonishing.

However, and that is why I'm posting, on Linux it kind of sucks. At least it is just another mediocre webcam. So if you're on Linux (and I guess you are, since you are here), I can't recommend paying for this.

Now, I could be wrong. Because, as forkandles said in his post:
> By the way, the Logitech Vision Pro is an excellent webcam and I can thoroughly recommend it.

He/you might be right. But please forkandles, can you explain how you get a decent picture quality from this webcam under Linux. Everything else works great. No drivers needed. Very good microphone that just works on 9.04.

---

