---
title: "Audio Sync Issues"
date: 2010-01-10
forum: Multimedia Software
---

### Post by paragonconcept on 2010-01-10
I'm having some weird audio issues. My system audio seems to be delayed. Even Turning down the volume has a 3 second lag from when the slider moves, and when the volume actually changes. 

Watching videos, the audio slowly falls behind the video, and after a few minutes its unwatchable. 

It does it in VLC, it does it in Boxee, it does it in Firefox through veetle, flash, etc.

Any ideas?

---

### Post by paragonconcept on 2010-01-10
it seems to degrade the longer the box is on. If i restart the machine, it doesnt happens as quickly. So  the further from boot the machine gets, the faster the audio falls out of sync....

---

### Post by paragonconcept on 2010-01-11
now my entire media library does it the second i start any video

---

### Post by paragonconcept on 2010-01-16
thanks....

---

### Post by Jeanaimart on 2010-03-13
I got the same problem...but just in Firefox when i'm watching Veetle streams. Don't know how to fix it

---

### Post by finnlloyd on 2010-04-24
[LEFT]I'm having the same issue with veetle streams and flock browser (as I can't get veetle working in firefox).   The audio is completely out of sync with video.  I'm using the 10.04 release candidate.
[/LEFT]

---

### Post by suli8 on 2010-04-25
im having the same issue!
on both firefox and chromium, veetle sound is poor and after 2 minutes it goes in delay of 3 seconds!
on veetle forum no body....and here??

---

### Post by truegrift on 2010-04-27
I am experiencing this problem as well, and it makes Veetle nearly unwatchable (i can still watch hockey with no sound). In running the Lucid Lynx release candidate on an Acer Aspire Revo nettop.

---

### Post by finnlloyd on 2010-04-28
I guess it is a problem with 64-bit operating systems/browsers.  On the veetle forums I saw a fix that suggested that we install the 32-bit versions of Firefox but I have no idea how to do that.  Here is the suggested solution however I do not know what it means or if it works.

**SOLUTION:** Install 32 bit  application on your 64 bit system. Trust me, it works without any issue.  I tried with Firefox 32, Chrome 32, Chromium-browser 32 etc... they all  work fine. To install 32 bit applications, you will have to use dpkg -i  --force-all (or --force-architecture or the like) and use getlibs to  install lacked 32bit libraries. It turned out to me that Firefox,  Chrome, Chromium 32 bit just works without using getlibs (it might be  because I installed 32 bit library already).

---

### Post by unattached on 2010-04-28
same here, veetle + 10.04 32bit!

worked for me on 9.10 32bit.. any help?

---

### Post by suli8 on 2010-04-29
well, i have karmic and 32 bit, and still have the prob.
so...
im almost sure its with pulse audio and vlc... but no solution so far...

---

### Post by bytie on 2010-05-02
Edited:

Dudes!
I've found a solution to this audio-video sync problem on 10.04.

Yes, it is caused by the vlc included with the veetle in the .veetle_vlc folder (thanks forevertheuni). Somewhat it leads to an audio delay in lucid systems, probably due to an output driver problem (I have encountered similar delay problems while this vlc was playing audio files when alsa, or pulse was selected as output driver). But oss driver worked for me.

Anyway, let's begin fixing it!

1) Firstly browse to the .veetle_vlc folder located in your home folder using nautilus (or your favourite file browser).

2) Rename the "vlc" file into something else. I have renamed it as "vlcori" which is the short for vlc original but you are free to give it any name at all.

3) Create a new document called vlc by right-clicking on the nautilus window, selecting "Create Document" and clicking "Empty File"

4) Now double click the vlc file you have created. The file be opened with gedit (or your default file editor).

5) Type (or copy-paste) the following code inside the file:

#! /bin/sh
exec ~/.veetle_vlc/vlcori --aout oss "$@"

6) If you renamed your original vlc file as something different than vlcori, make sure you have changed the code above according to the name you gave.

7) Save the file, close gedit, 

8 ) Right click the vlc file you have created, click "Properties", then "Permissions" tab, make sure "Allow executing file as program" is selected, if not click the checkbox beside it, and finally click "Apply"

9) Close nautilus, enjoy veetle.

---

### Post by scitizen17 on 2010-05-03
Thanks for this but in my case this causes my browser to freeze and gray-out when trying to play a file in Veetle. I renamed the vlc file the same as you and I changed "yego" to the name of my machine.

Any help?

> **bytie said:**
> Dudes!
I've found a solution to this audio-video sync problem of veetle on 10.04.

Yes, it is caused by the vlc included with the veetle in the .veetle_vlc folder (thanks forevertheuni). Somewhat it leads to an audio delay in lucid systems, probably due to an output driver problem (I have encountered similar delay problems while this vlc was playing audio files when oss, alsa, or pulse was selected as output driver). But sdl driver worked for me.

Anyway, let's begin fixing it!

1) Firstly browse to the .veetle_vlc folder located in your home folder using nautilus (or your favourite file browser).

2) Rename the "vlc" file into something else. I have renamed it as "vlcori" which is the short for vlc original but you are free to give it any name at all.

3) Create a new document called vlc by right-clicking on the nautilus window, selecting "Create Document" and clicking "Empty File"

4) Now double click the vlc file you have created. The file be opened with gedit (or your default file editor).

5) Type (or copy-paste) the following code inside the file:

#! /bin/sh
exec /home/yego/.veetle_vlc/vlcori --aout sdl "$@"

6) If you renamed your original vlc file as something different than vlcori, make sure you have changed the code above according to the name you gave.

7) Save the file, close gedit, close nautilus, enjoy veetle.

---

### Post by truegrift on 2010-05-03
> **scitizen17 said:**
> Thanks for this but in my case this causes my browser to freeze and gray-out when trying to play a file in Veetle. I renamed the vlc file the same as you and I changed "yego" to the name of my machine.

Any help?

This is the same issue that I am having. FYI, I installed Mythbuntu last night, and Veetle worked flawlessly.
Any help is appreciated, this seems to be a common problem no?

---

### Post by scitizen17 on 2010-05-03
I made some progress after reading a thread on the Veetle forum. You have to set the new file, "vlc" to be executable. Right click on the file, click Properties, click Permissions tab, check the box for "Allow executing file as program"

Although it is now 'almost' in sync, and a lot better than it was, now it seems as though the audio track is about 1/10 of a second AHEAD of the video.

It is much better though and watchable.

> **truegrift said:**
> This is the same issue that I am having. FYI, I installed Mythbuntu last night, and Veetle worked flawlessly.
Any help is appreciated, this seems to be a common problem no?

---

### Post by bytie on 2010-05-04
Please update the vlc file you have created according to my edited post.

Now the sound is not in advance of the video, because "oss" is used as the default instead of "sdl",
You don't have to insert your user name inside the code and,
The necessary information regarding to making the file you have created as executable is included.

So the edited instructios shall work perfectly for everyone.

---

### Post by finnlloyd on 2010-05-09
bytie thanks for your edit.  Veetle in Flock are now working!  Has anybody got it to work in Firefox or Chromium?

---

### Post by alikara on 2010-05-09
Thanks bytie. 
I had same disgusting issue, but it works now. (10.04 LTS)

---

### Post by bytie on 2010-05-10
> **finnlloyd said:**
> bytie thanks for your edit.  Veetle in Flock are now working!  Has anybody got it to work in Firefox or Chromium?

Your system should be 64 bit am I wrong?

Veetle's plugin is just for 32 bits. And Flock is a 32 bit browser.
That's the reason it's working in flock, but not in firefox or chromium in a 64 bit system.

---

### Post by finnlloyd on 2010-05-11
> **bytie said:**
> Your system should be 64 bit am I wrong?

Veetle's plugin is just for 32 bits. And Flock is a 32 bit browser.
That's the reason it's working in flock, but not in firefox or chromium in a 64 bit system.

you are correct bytie.  I am running a 64 bit system.  Thanks again for help in getting it working.

---

### Post by Pykler on 2010-05-24
> **bytie said:**
> Edited:
#! /bin/sh
exec ~/.veetle_vlc/vlcori --aout oss "$@"

6) If you renamed your original vlc file as something different than vlcori, make sure you have changed the code above according to the name you gave.


This fixed it great :)

I have Ubuntu 10.04 64bit, I installed swiftfox amd64_32bit (amd64 for 32bit os), when it starts it complains about the 64 bit plugins, but that's OK. Installing Veetle from veetle.com allows playing of veetle in swiftfox but with a 3 second (or 4 second) audio delay. Using the oss output for audio removes the audio delay. Awesome!!!! :guitar:

---

### Post by Basti4n on 2010-06-06
Sorry to bother. I'm new to the forum and also linux. :S
I just installed Veetle in Lucid 10.04 using sh. I can see streams on veetle but I experience the weird audio/video bad sync.
I have been looking for the 'veetle_vlc' forlder wothout results. I really don't know where to find it.
Any help??
Thanks a lot.
Seba.

> **bytie said:**
> Edited:

Dudes!
I've found a solution to this audio-video sync problem on 10.04.

Yes, it is caused by the vlc included with the veetle in the .veetle_vlc folder (thanks forevertheuni). Somewhat it leads to an audio delay in lucid systems, probably due to an output driver problem (I have encountered similar delay problems while this vlc was playing audio files when alsa, or pulse was selected as output driver). But oss driver worked for me.

Anyway, let's begin fixing it!

1) Firstly browse to the .veetle_vlc folder located in your home folder using nautilus (or your favourite file browser).

2) Rename the "vlc" file into something else. I have renamed it as "vlcori" which is the short for vlc original but you are free to give it any name at all.

3) Create a new document called vlc by right-clicking on the nautilus window, selecting "Create Document" and clicking "Empty File"

4) Now double click the vlc file you have created. The file be opened with gedit (or your default file editor).

5) Type (or copy-paste) the following code inside the file:

#! /bin/sh
exec ~/.veetle_vlc/vlcori --aout oss "$@"

6) If you renamed your original vlc file as something different than vlcori, make sure you have changed the code above according to the name you gave.

7) Save the file, close gedit, 

8 ) Right click the vlc file you have created, click "Properties", then "Permissions" tab, make sure "Allow executing file as program" is selected, if not click the checkbox beside it, and finally click "Apply"

9) Close nautilus, enjoy veetle.

---

### Post by Basti4n on 2010-06-07
Hey sorry..
I'm new to this... and I can't find the folder 'veetle_vlc' which you mention even if I have installed veetle using the 'veetle-0.9.17-linux-install.sh'.
Any help!?!??
Thx

> **bytie said:**
> Edited:

Dudes!
I've found a solution to this audio-video sync problem on 10.04.

Yes, it is caused by the vlc included with the veetle in the .veetle_vlc folder (thanks forevertheuni). Somewhat it leads to an audio delay in lucid systems, probably due to an output driver problem (I have encountered similar delay problems while this vlc was playing audio files when alsa, or pulse was selected as output driver). But oss driver worked for me.

Anyway, let's begin fixing it!

1) Firstly browse to the .veetle_vlc folder located in your home folder using nautilus (or your favourite file browser).

2) Rename the "vlc" file into something else. I have renamed it as "vlcori" which is the short for vlc original but you are free to give it any name at all.

3) Create a new document called vlc by right-clicking on the nautilus window, selecting "Create Document" and clicking "Empty File"

4) Now double click the vlc file you have created. The file be opened with gedit (or your default file editor).

5) Type (or copy-paste) the following code inside the file:

#! /bin/sh
exec ~/.veetle_vlc/vlcori --aout oss "$@"

6) If you renamed your original vlc file as something different than vlcori, make sure you have changed the code above according to the name you gave.

7) Save the file, close gedit, 

8 ) Right click the vlc file you have created, click "Properties", then "Permissions" tab, make sure "Allow executing file as program" is selected, if not click the checkbox beside it, and finally click "Apply"

9) Close nautilus, enjoy veetle.

---

### Post by Ramiro Franco on 2010-06-22
Hi Basti4n

        you should not forget the "." at the beginning of the directory name. I it was installed in your home directory you can type

       cd ~/.veetle_vlc ; ls  

and you would see the files there

---

### Post by majedaly on 2010-07-02
Thanks, this solved the veetle sync issues instantly on Lucid :)

---

### Post by ryouji_shiki on 2010-07-03
now with an Ubuntu update this **bytie** solution doesn't work anymore U_U... any ideas would be highly appreciated....

---

### Post by dingo on 2010-07-09
Thanks for this thread. Editing the ~/.veetle_vlc folder as described above solved my veetle audio sync issue on 10.04. 

One slight addition: I added the 'padsp' command to wrap the vlc output and send it through pulseaudio. This allowed me to use my external usb speakers to listen to veetle streams, and also allows other applications to play sounds while veetle is streaming.

Here's how the vlc command looks with 'padsp' added:

```
exec padsp ~/.veetle_vlc/vlc_bin --aout oss "$@"
```

---

### Post by ChannelZ28 on 2010-07-18
thanks, i was having the same veetle and the above solution fixed it. i really appreciate the instructions.

i just have one question, what did it actually do? i like learning about linux through my problems, instead of just blindly following commands, i like to know what they actually mean.

could someone give a quick (simple) description of what i actually did and why it works?
thanks.

---

### Post by leebh28 on 2010-07-22
Hi Bytie,

New Ubuntuian here.
Thank you for the great solutions, it worked for 10.4. Dual Boot with Windows Vista Home.
FYI, this solution worked on Chrome, but not firefox. 

Cheers!:popcorn:


> **bytie said:**
> Edited:

Dudes!
I've found a solution to this audio-video sync problem on 10.04.

Yes, it is caused by the vlc included with the veetle in the .veetle_vlc folder (thanks forevertheuni). Somewhat it leads to an audio delay in lucid systems, probably due to an output driver problem (I have encountered similar delay problems while this vlc was playing audio files when alsa, or pulse was selected as output driver). But oss driver worked for me.

Anyway, let's begin fixing it!

1) Firstly browse to the .veetle_vlc folder located in your home folder using nautilus (or your favourite file browser).

2) Rename the "vlc" file into something else. I have renamed it as "vlcori" which is the short for vlc original but you are free to give it any name at all.

3) Create a new document called vlc by right-clicking on the nautilus window, selecting "Create Document" and clicking "Empty File"

4) Now double click the vlc file you have created. The file be opened with gedit (or your default file editor).

5) Type (or copy-paste) the following code inside the file:

#! /bin/sh
exec ~/.veetle_vlc/vlcori --aout oss "$@"

6) If you renamed your original vlc file as something different than vlcori, make sure you have changed the code above according to the name you gave.

7) Save the file, close gedit, 

8 ) Right click the vlc file you have created, click "Properties", then "Permissions" tab, make sure "Allow executing file as program" is selected, if not click the checkbox beside it, and finally click "Apply"

9) Close nautilus, enjoy veetle.

---

### Post by aalto on 2010-08-14
Hi,

I had the sync problem too on Lucid and the oss-trick didn't help. However, I was able to fix the problem by changing the script a bit:

```
exec ~/.veetle_vlc/vlc_w --alsadev 0 "$@"
```

So, for some reason stating the alsa device explicitly helps. Go figure.

---

### Post by trigg3rtrigg3r on 2010-08-28
[bytie]("http://ubuntuforums.org/member.php?u=1065341") 's solution, worked great.
thanks a lot.
cheers

---

### Post by jcneto on 2010-09-10
I used **Dingo**'s command over the **bytie** solution with Lucid and it works perfect.

Thanks!!!

---

### Post by Arex Bawrin on 2010-09-26
> **aalto said:**
> Hi,

I had the sync problem too on Lucid and the oss-trick didn't help. However, I was able to fix the problem by changing the script a bit:

```
exec ~/.veetle_vlc/vlc_w --alsadev 0 "$@"
```

So, for some reason stating the alsa device explicitly helps. Go figure.

This solution has worked the best for me BUT there is just a small audio delay (not as bad as it was before). Is there anymore adjustments I can make?

---

### Post by apexofservice on 2010-11-14
Someone asked to explain what this fix did.  Broadly, something in veetle is going to call the code found in ~/.veetle_vlc/vlc.  That file is a binary.  What this fix does is put a shell script where vlc used to be.  The shell script just calls the code that veetle was going to call, but appends the argument --oss or --alsadev to the call (the former worked for me).  That argument sets some sort of parameter relating to some software for sound.  Graphically, 

old way:  veetle ->  vlc
new way:  veetle -> vlc-altered -> vlc-original --oss 

The --oss or --alsadev option is what's really doing the fix in all this. We just inserted a link into the call chain.   

I think the way to actually "fix" this would be to find out more about when veetle was going to call vlc, and have it add the --oss or whatever option at that point, if possible.  But I was just glad to have sound sync back, so I didn't investigate more.

---

### Post by Z06Gal on 2010-11-19
None of these fixes worked for me on ubuntu 10.10.  Please post if someone has another idea.  Thanks.

---

### Post by Z06Gal on 2010-11-19
I found something on the veetle forums that worked great.  Open terminal and put in sudo apt-get autoremove pulseaudio  My sound is now synced perfectly.  ;)

---

### Post by anlag on 2011-01-08
> **aalto said:**
> Hi,

I had the sync problem too on Lucid and the oss-trick didn't help. However, I was able to fix the problem by changing the script a bit:

```
exec ~/.veetle_vlc/vlc_w --alsadev 0 "$@"
```

So, for some reason stating the alsa device explicitly helps. Go figure.

This made the fix work for me, thanks a lot to everyone who contributed and let me watch the second half of Arsenal-Leeds in synch (Leeds Leeds Leeds!)

---

### Post by eakergd on 2011-02-02
> **aalto said:**
> Hi,

I had the sync problem too on Lucid and the oss-trick didn't help. However, I was able to fix the problem by changing the script a bit:

```
exec ~/.veetle_vlc/vlc_w --alsadev 0 "$@"
```So, for some reason stating the alsa device explicitly helps. Go figure.


This fix worked best for me, but now my sound is actually slightly ahead of the video by about half a second.  Any way to manually delay or adjust the audio in veetle?

---

### Post by redseventyseven on 2011-03-30
> **Arex Bawrin said:**
> This solution has worked the best for me BUT there is just a small audio delay (not as bad as it was before). Is there anymore adjustments I can make?

A little late to the party, I know, but I hope someone finds this useful!

You can use the audio-desync parameter to make any fine-tuning adjustments. In my case, this works:

```
exec ~/.veetle_vlc/vlcori --alsadev --audio-desync=500 0 "$@"
```

---

### Post by christoff2008 on 2011-04-04
You werent too late, it works!

Now if I could only stop veetle from freezing my keyboard!!:guitar:

---

### Post by idjrox on 2011-05-09
OK!...finally got it working perfectly in sync on 10.10 ..this should also work for 11.04. its really simple :

1-open terminal

2-in terminal type or copy (CTRL+SHIFT+V to paste in terminal): sudo apt-get autoremove pulseaudio

3-ENJOY!! 

thats it ...apparently pulseaudio is interfering with veetle ..dont ask me how or why ..but it works...

---

### Post by demilord on 2011-05-10
isnt that a little to much removing pulseaudio.. it might be a bug in the program instead of pulseaudio....

---

### Post by em4mapson on 2011-11-18
Old topic, but I had this issue with 10.10 and found the solution. Just though others might appreciate it too

[http://s1.veetle.com/forums/viewtopic.php?f=7&t=2312#p8845](http://s1.veetle.com/forums/viewtopic.php?f=7&t=2312#p8845)

Please note that I am using 32bit not 64bit, but problem solved...

---

### Post by minnish0831 on 2012-08-26
Having this issue with Veetle too. I'm using 12.04 ubuntu and Veetle 0.9.17. Can someone help me in how to use this code mentioned above and does it still work?

---

### Post by oldos2er on 2012-08-27
Please start a new thread for your question, minnish0831, this one's old.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

