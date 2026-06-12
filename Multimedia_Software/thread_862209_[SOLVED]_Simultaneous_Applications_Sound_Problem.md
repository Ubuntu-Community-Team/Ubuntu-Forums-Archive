---
title: "[SOLVED] Simultaneous Applications Sound Problem"
date: 2008-07-17
forum: Multimedia Software
---

### Post by ragflan on 2008-07-17
Hey. I'm under Ubuntu Hardy Heron.

Individually, everything has sound. For example when I play videos or DVDs through VLC or any other player, sound is normal. When I run youtube videos or any other streaming media, sound is normal.

But when VLC is running something, I cannot hear anything from YouTube or any other streaming sites. Even if VLC is not playing (with media loaded but in paused state), I still cannot hear anything from YouTube sites. Video plays but no sound. 

I tried with Firefox, Opera and Epiphany with same results. The opposite is true as well. If I open YouTube videos first, then open VLC, there's no sound on VLC or Totem.

Also, I cannot hear any sound from Streaming Media** even if I close VLC and reload the page**. I need to restart the browser window session, and then I can hear sound from streaming media. 

I can hear sounds from different streaming media in the same browser window (in different tabs) and I can even hear sounds between different browsers. Like I can play media in Firefox and in Opera and no conflicts. 

Is this normal?

---

### Post by marcordenis on 2008-07-17
I have the same problem... I have tried editing all sorts of files, all to no avail. 
I found something out that I don't think I've seen mentioned anywhere: if you create a new user account and log in to that account, it can play sound simultaneously in different applications. 
Could someone maybe develop that and try to explain why it works in one account and not the other? BTW I don't feel like migrating everything to another account because it is too complicated for something probably very simple.
Thanks for any answers, solutions or workarounds of any sort.

---

### Post by markbuntu on 2008-07-17
If something works in one account and not another, there are differences in the hidden configuration files in the /home folders of each. A new user is set up with  default configurations which are most likely different from the initial user configurations which come from the iso on initial installation.

If you have a lot of time, you could go through these and compare them to parse the differences and test them and maybe find the solution to this. A lot of people would be very grateful to anyone who did this.

---

### Post by marcordenis on 2008-07-17
I have solved my problem and I did more or less what you said...
I think this annoys other people than me, and so I will explain step by step. I don't know if this way is safe, good or whatever but it helped me and it also helped a friend of mine. I cannot guarantee this works, so do this at your own risk.
So... the first thing I did was make a new user account under System - Admin - Users and Groups. Then I went into a file browser with root privileges (sudo nautilus in the terminal). I went into /home/[me] and made a new folder. I just took all the hidden files from my home folder and put them into the backup folder I had just made. Then, I went into /home/[test acc] and took all the hidden files from that home folder and copied them into my own. Then I went into the backup folder and copied everything back into my home folder. It will prompt you to overwrite. Say "Skip All", so do not overwrite. Then I restarted and it just worked. 
I don't know exactly what is responsible for the change, but with me and my friend the change happened. 
Also, under System - Preferences - Sound the first three options should be on Autodetect and the fourth one on ALSA.
Oh yeah and you can delete the test account once you are done, nothing is dependent on it.
I hope this helps.
UPDATE:
 I just noticed that on login I got the error "User's $HOME/.dmrc filde is being ignored." etc. etc. I solved this problem with this thread, [http://ubuntuforums.org/showthread.php?t=491591](http://ubuntuforums.org/showthread.php?t=491591), the last post helped me out, I don't know what it does but the message disappears.

---

### Post by ragflan on 2008-08-12
I think this problem is solved. You need to set your Audio Output module to ALSA and then it works fine. I read somewhere that 2 different programs are not able to use the soundcard at the same time, so this ALSA thing will resolve that problem.

Under VLC for example:
1.) Open VLC Media Player.
2.) Click on Settings --> Preferences.
3.) Expand Audio section (from the menu on the right.)
4.) You'll see Filters, Output Modules, Visualizations.
5.) Click on Output Modules.
6.) From the drop-down menu, select ALSA audio output.

Now, test it. I'm playing a video on VLC and streaming a video on YouTube and both have sound.

---

### Post by markbuntu on 2008-08-12
If you want to get all your sound applcations to play together, go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

