---
title: "Flash no Sound - 7.10"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by Spyderizer on 2007-10-20
Hi

Lost Flash Sound after installing 7.10. When installing, the old /home was left intact. (everything else was clean)

Troubleshooting:

Created a new user, it didn't find the plugin when attempting to access flash content so firefox asked for an install, installed flash-nonfree, restarted firefox and everything worked fine.

Ah ha, I says! Problem with /home folder.

So I switch back into my own account, get rid of all the .mozilla*, .firefox*, .macromedia ect ect. Even got rid of flash-nonfree so to recreate all the conditions that made it work in this other account.

Went to access some flash content, got prompted to install the plugin, did so, restarted the browser, cleared the cache, went to the flash content and...no sound.

What did I miss?

---

### Post by SteinbergerNate on 2007-10-21
I too have just discovered this problem. Flash movies (youtube, homestarrunner.com, etc.) show up just fine but have no sound at all. I'm working with a clean install.

---

### Post by NilsE on 2007-10-21
Installing the flash plugin when prompted did not work for me on first install of Gutsy.

I had to uninstall it and then install flashplugin-nonfree via synaptic.

---

### Post by rare HERO on 2007-10-22
How do you uninstall and reinstall?  Please be specific.

---

### Post by Libertine on 2007-10-23
I had this problem but it was fixed by this: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_PulseAudio_Sound_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_PulseAudio_Sound_Server)

Let me know if it works!

---

### Post by TryMe on 2007-10-23
run command in terminal window
```
lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`
```

does the sound device have PCI Id 8086:284b

if so ALSA sound is likely to blame bug # 131133[  (link)]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133")

I have same issue only OSS seems to work for my intel sound. I think there must be a way to direct flash to OSS. Anyway there is a wiki entry [(link)]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")  but I am not totally sold on compiling ALSA drivers when OSS works in sound preferences  test.

---

### Post by TryMe on 2007-10-23
I read Spyderizer post again and I confirm that flash sound works under a newly created user but not original account. Problem must lie in the  /home folder.

---

### Post by TryMe on 2007-10-23
I am sure some one will be able to explain exactly which setting folder does the trick but it won't be me. This is what I did and it worked. If you have a more direct... less ham fisted way please share.

Fix:
open Nautilus to your home folder
make a folder called settings
press ctr + H or go to the view menu and select “show hidden files”
cut & paste all hidden folders (the ones beginning with  “.”) except  “.trash” to the settings folder we just made.
reboot
 after reboot and login ubuntu  should ask you to run these commands
```
 asoundconf list
 asoundconf set-default-card <name of sound card>
```

open Nautilus to your home folder
press ctr + H or go to the view menu and select “show hidden files”
delete the newly created hidden folders  (except  “.trash)
Then  just copy the original hidden folders from the settings folder  back to your home folder
reboot again

Flash sound should be working. enjoy.

---

### Post by rare HERO on 2007-10-27
> **TryMe said:**
> run command in terminal window
```
lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`
```

does the sound device have PCI Id 8086:284b

if so ALSA sound is likely to blame bug # 131133[  (link)]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133")

I have same issue only OSS seems to work for my intel sound. I think there must be a way to direct flash to OSS. Anyway there is a wiki entry [(link)]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")  but I am not totally sold on compiling ALSA drivers when OSS works in sound preferences  test.

```
$ lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`
grep: 00:06.0: No such file or directory
grep: 01:0b.0: No such file or directory

```

---

### Post by TryMe on 2007-10-27
rare HERO do you have any sound at all?

---

### Post by amheuwr on 2007-10-27
[FONT="Arial"][SIZE="2"]I have the same problem as many others in that there is no sound with flash when using my profile. It is enabled for sound in users/groups. When I log into one of the other profiles sound straight away.
I have tried deleting the .Mozilla directory so a new one is created. No good. Reinstalled Firefox. No good.

 run > lspci -n | grep `lspci | grep -i audio | awk '{print $1}'` and got the same result as tryme. 

If I don't fix this soon I will start banging my head against the wall. I am on the verge of doing a fresh install of Gutsy which seems a bit drastic just to fix this problem. I upgraded from 7.04 to 7.10 about a week ago. Sound was working great in Feisty. [/SIZE][/FONT]

---

### Post by TryMe on 2007-10-28
The problem I think is in the .gnome .gnome2  .gnome2_private  folders. They are some how preventing the proper setup of ALSA.
You might try renaming these folders and rebooting

---

### Post by amheuwr on 2007-10-28
> **TryMe said:**
> The problem I think is in the .gnome .gnome2  .gnome2_private  folders. They are some how preventing the proper setup of ALSA.
You might try renaming these folders and rebooting
[SIZE="2"]
Tried all the above with no luck. Tried renaming them individually then restarting Gnome. No difference. Then rebooting, again no difference. Did the same thing again but this time renaming all the gnome folders. Again no difference found. Have now restored all the old folders to their original names. 

There is obviously something somewhere in my profile folders doing this but I am not technical enough to find out what it is.

Other things I have tried are completely removing all the sound files such as alsa and oss, the flash players, then re installing them again. [/SIZE]

---

### Post by christianxxx on 2007-10-28
This is just making me nuts!
The proposed solution didn't do anything here. "asoundconf list" didn't produce anything, so there was none to set as default.

Reinstall?


Christian

---

### Post by amheuwr on 2007-10-28
[SIZE="3"]I located a solution [[COLOR="DarkRed"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=3446685") which works for me. Yipee:)

> 
**dentaku65**
FIXED!
Code:

 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old

Restart FF and ....tak flash audio is working!!

My only concern is that the fix was posted October 2005. If this sort of problem was known about then why is it still happening? 
[/SIZE]

---

### Post by TryMe on 2007-10-28
amheuwr Like I said before I moved all my config folders to a new directory then rebooted. So the .gnome folders were just a guess. I only know that moving all the config folders worked for me but beyond that i don't know the exact ones causing the issue.. sorry :(

christianxxx It does seem odd that "asoundconf list" did not list any sound cards so I wonder if your card is  just unsupported by ALSA? As far as I can tell reinstalling isn't going to help unless your planning to format your home directory. (not recommended)

Maybe you could create a new admin user and copy you data over. Hopefully someone else will come up with the real cause and solution.

edit: looks like amheuwr may have done that already.

---

### Post by rare HERO on 2007-10-28
> **rare HERO said:**
> Here is what I did to solve my problem.

Updated firefox to 2.0.0.8

```
$ ubuntuzilla.py -a install -p firefox
```

List my soundcard devices
```
$ gksudo asoundconf list
```

Choose the one I want as default
```
$ gksudo asoundconf set-default-card Audigy2
```

Edit firefox so it takes alsa
```
$ gksudo gedit /etc/firefox/firefoxrc
```

Text editor comes up.  Change:
FIREFOX_DSP=&#8221;none&#8221;

To:
FIREFOX_DSP=&#8221;alsa&#8221;

Check sound properties and make sure everything is set to ALSA in the window that comes up:
```
$ gnome-sound-properties
```

:)

---

### Post by christianxxx on 2007-10-28
> **TryMe said:**
> 
christianxxx It does seem odd that "asoundconf list" did not list any sound cards so I wonder if your card is  just unsupported by ALSA? As far as I can tell reinstalling isn't going to help unless your planning to format your home directory. (not recommended)

Maybe you could create a new admin user and copy you data over. Hopefully someone else will come up with the real cause and solution.


The thing that really blows my mind is that everything worked fine in Feisty, it's just after the update that this occured. 
Everything I do suggests that my card isn't supported by ALSA, and that OSS is my only way of getting sound. 

Whish this would just work again. Unfortunately I never confirmed sound after the upgrade. I was too busy checking out the new features... :)


Christian

---

### Post by billybag on 2007-10-29
im having the same issues. everything worked fine in feisty and then i updated to gutsy and the sound in firefox just doesnt work anymore. havent been able to find a fix yet

sound doesnt appear to work in opera either

---

### Post by amheuwr on 2007-10-29
ChristianXXX
Have a look at this [[COLOR="DarkRed"]**thread.**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449") I have learned quite a bit working through the guide.:-)

---

### Post by amheuwr on 2007-10-29
Billybag
Have you tried the fix at entry [[COLOR="DarkRed"]**#15**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3653322&postcount=15") in this thread?  I found it in an old thread going back to 2005. It worked a treat for me, and your problem seems pretty much  the same as I suffered.](*,)

---

### Post by patis on 2007-10-30
I'm stuck with the same problem: No sound in Firefox flash, i.e., Youtube, and no sound in Totem. But Rythmbox works well, and VLC as well after telling it to pick the right sound device.

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: U0x47f0xc001 [USB Device 0x47f:0xc001], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio
```

System-->Preferences-->Sound, "Devices" tab, lists USB as the default device, and the test buttons they all work, I can hear the test tone on my USB headphones.

So what else does Totem need to work? Isn't it supposed to pick up the sound device from the global sound configuration? And flash, I don't know.

IIt all worked well on Feisty before the upgrade.

---

### Post by quickshade on 2007-10-30
quick suggestion. Run firefox as a root user and go onto youtube and play a video. Check your terminal for any errors. I figured out that my pulse audio engine wasn't working properly. No clue why but I had to uninstall it along with a couple of programs and then reinstall firefox. Fixed it for me. I know it sucks, I wasted 5 days trying to figure this out.

---

### Post by christianxxx on 2007-10-30
> **quickshade said:**
> quick suggestion. Run firefox as a root user and go onto youtube and play a video. Check your terminal for any errors. 

Ok, I tried this. It was kind of interesting, though I don't know what to make of it. But maybe someone else here do?
Here is the response in the terminal:

```

ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:768:(parse_card) cannot find card 'ICH4'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device

```

Since last post, I've tried to compile and install the ALSA-drivers, as the ALSA homepage clearly states support for ICH4 (my card). But the modprobe failed, and I suspect the error above has something to do with that, but with my limited knowledge of linux, I really don't know.


Christian

---

### Post by Tom B on 2007-10-30
Sound has not been working for me from flash or from VLC media player. I tried running firefox (swiftfox, actually) as root, and playing a video, and it gave me this ```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
``` for as long as I played the video. When I try to play something with vlc it gives me ```
 [00000354] oss audio output error: cannot open audio device (/dev/dsp)
[00000354] main audio output error: couldn't find a filter for the conversion
[00000354] main audio output error: couldn't create audio output pipeline

```
 Any ideas?

Edit: Also, now whenever I run swiftfox, it doesn't have any of my preferences. Is it still running as root for some reason? What did I do?

---

### Post by billybag on 2007-10-30
> **amheuwr said:**
> Billybag
Have you tried the fix at entry [[COLOR="DarkRed"]**#15**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3653322&postcount=15") in this thread?  I found it in an old thread going back to 2005. It worked a treat for me, and your problem seems pretty much  the same as I suffered.](*,)


nah it didn't seem to work. of course things could be a bit more screwed up now in the midst of trying other suggestions and 'fixes'

---

### Post by MystaMax on 2007-11-05
[quote=dentaku65][SIZE=3]
FIXED!
Code:

 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old

Restart FF and ....tak flash audio is working!!
[/SIZE][/quote][SIZE=3]

[amheuwr's post]("http://ubuntuforums.org/showpost.php?p=3653322&postcount=15"), worked for me. 

I should add that I did a fresh install of gutsy, but kept my /home partition from feisty. Sound worked fine @ first, but I wanted to use the latest flash player update. I tried to install the latest update, which then killed the sound. I uninstalled the latest update,and reinstalled from the repositories, and still had no sound; found this post tried it, and it now it works!

I have a  Creative Labs SB Audigy (rev 03). It'd be helpful if everyone posted which card they have.

Thanks!
[/SIZE]

---

### Post by strungoutfan78 on 2007-11-29
i'd just like to touch on this subject and bring up the question of whether or not anyone with this same sound problem is also using pulseaudio installed from the repos.  i too do not have sound in any flash applications or totem.  not sure why but i do know that if i want sound all i have to do is
```
neil@neil-laptop:~$ killall pulseaudio
```

and thats it.  sound works.
just wondering if anyone else finds this to be true.

---

### Post by Tom B on 2007-11-29
Wow. I was having problems with amarok hanging whenever I paused anything. Someone else on the forums had the same problem and removed pulseaudio to fix it, so I did as well. Now, amarok and flash sound work. I swear I installed pulseaudio to try and fix this problem. Oh well, I'm glad it works now. I'm still having problems with VLC though, it's giving me something about not being able to open up a DVD when I try to play an mp3 file. I'll try to figure that out, too. So, anyone else having this problem, try uninstalling pulseaudio.

---

### Post by billybag on 2007-11-30
its funny because their is another forum under ubuntuforums that touches on the same subject as this one and it says installing pulse audio FIXES the problem. anyway, nothing has worked for me thus far. i have given up. i am just going to wait until i can afford a new computer and install a fresh ubuntu install.

---

### Post by llamakc on 2007-12-02
> **strungoutfan78 said:**
> i'd just like to touch on this subject and bring up the question of whether or not anyone with this same sound problem is also using pulseaudio installed from the repos.  i too do not have sound in any flash applications or totem.  not sure why but i do know that if i want sound all i have to do is
```
neil@neil-laptop:~$ killall pulseaudio
```and thats it.  sound works.
just wondering if anyone else finds this to be true.

Thanks. This worked for me too.

---

### Post by strungoutfan78 on 2007-12-02
no problem.  just wish i knew why this is so.:(

---

### Post by BandD on 2007-12-02
I've spent the better part of two weeks trying to get my sound all straightened out.  I'm a fairly new Linux user and the things I was trying were way over my head.  

The original problem I was trying to solve was an issue with my mic.  I kept getting errors messages when I was trying to test it.  I couldn't get Skype to use the mic.  I was very frustrated.  

Then I read some posts about people who had trouble with flash.  And I thought, well, jeez, I haven't even tested that yet.  So I went to youtube, and to addictinggames and nothing.  I was so peeved!

Then today, I googled 'hda alsa flash no sound' and this thread was at the top of the list.  So I thought what the hey, uninstalling an application is easy.  Let's try it.  

Now EVERYTHING works!  What an easy fix that was.  I still can't understand why this is an issue.  Pulse is supposed to make the sound device available to all programs, but it seems to make the resource busy so no one can use it. 

Just for reference, I have an Intel HDA ICH6 Realtex ALC260 sound card set up in a Sony Viao VGN-FS260.  I've also updated the ALSA drivers to the most recent 1.0.15.

Anyway, PROBLEM SOLVED!

---

### Post by llamakc on 2007-12-02
> **BandD said:**
> I've spent the better part of two weeks trying to get my sound all straightened out.  I'm a fairly new Linux user and the things I was trying were way over my head.  

The original problem I was trying to solve was an issue with my mic.  I kept getting errors messages when I was trying to test it.  I couldn't get Skype to use the mic.  I was very frustrated.  

Then I read some posts about people who had trouble with flash.  And I thought, well, jeez, I haven't even tested that yet.  So I went to youtube, and to addictinggames and nothing.  I was so peeved!

Then today, I googled 'hda alsa flash no sound' and this thread was at the top of the list.  So I thought what the hey, uninstalling an application is easy.  Let's try it.  

Now EVERYTHING works!  What an easy fix that was.  I still can't understand why this is an issue.  Pulse is supposed to make the sound device available to all programs, but it seems to make the resource busy so no one can use it. 

Just for reference, I have an Intel HDA ICH6 Realtex ALC260 sound card set up in a Sony Viao VGN-FS260.  I've also updated the ALSA drivers to the most recent 1.0.15.

Anyway, PROBLEM SOLVED!

For the rest of the people you did not say what you uninstalled.

---

### Post by Tom B on 2007-12-02
I'm assuming it was pulseaudio. That's what worked for me.

---

### Post by strungoutfan78 on 2007-12-03
ok so now that i see several people have successfully remedied their sound issues by removing pulseaudio i figured i'd give it a go.  now i seem to have no issues with my flash movie sound nor any issues with totem.  what i am NOW missing is all my system sounds and the previews of my audio files (both i miss very much).  as i am writing this, though , i have also noticed that esound is not installed on my system (only esound-client).  oops](*,)   maybe i'm jumping the gun here.  we'll see.

---

### Post by strungoutfan78 on 2007-12-03
ok, so it seems my problem the whole time was not having esound properly installed. it may sound stupid but i would recommend checking whether or not the package "esound" is installed.  seems by default i only had "esound-client"  installed, which was only half of what i needed.  hhope this helps someone.:guitar:

**EDIT**
seems esound probably was installed by default.  i didn't realize that when installing pulseaudio apparently something replaces esound and it is removed.  i was under the impression that the "pulseaudio-esound-compat" was a daemon that worked in conjunction WITH esound.  guess not?:?::?:

---

### Post by SpiXe on 2008-03-21
> **TryMe said:**
> I am sure some one will be able to explain exactly which setting folder does the trick but it won't be me. This is what I did and it worked. If you have a more direct... less ham fisted way please share.

Fix:
open Nautilus to your home folder
make a folder called settings
press ctr + H or go to the view menu and select “show hidden files”
cut & paste all hidden folders (the ones beginning with  “.”) except  “.trash” to the settings folder we just made.
reboot
 after reboot and login ubuntu  should ask you to run these commands
```
 asoundconf list
 asoundconf set-default-card <name of sound card>
```

open Nautilus to your home folder
press ctr + H or go to the view menu and select “show hidden files”
delete the newly created hidden folders  (except  “.trash)
Then  just copy the original hidden folders from the settings folder  back to your home folder
reboot again

Flash sound should be working. enjoy.

Ive spent some time finding a way to make the sound work. This works!! Except i had to type the commands by myself after rebooting ^^, Thanks !!!!! :D:D:D

---

### Post by dvord on 2008-04-30
I type in 

asoundconf list

And nothing is returned.

---

### Post by TryMe on 2008-04-30
> **dvord said:**
> I type in 

asoundconf list

And nothing is returned.

Do you have any sound at all???

---

### Post by dvord on 2008-04-30
Yes system sounds work fine.  MP3's play fine too.

Bah, I just realized this is a 7.10 thread I'm using 8.04

---

### Post by TryMe on 2008-05-01
Oh, in that case try this thread:
[http://ubuntuforums.org/showthread.php?t=204022]("http://ubuntuforums.org/showthread.php?t=204022")

---

### Post by Svantevid on 2008-05-14
Aaaaah this little thing finaly worked for me

>  asoundconf list
 asoundconf set-default-card <name of sound card>

---

