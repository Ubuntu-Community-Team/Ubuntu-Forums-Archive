---
title: "Was trying to watch a move right now and got myself into a bit of a jam - pleas help"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ClientAlive on 2011-04-03
Hi everyone,

I'm running Ubuntu 11.04, have mplayer and smplayer as the gui for it. I was trying to watch a certain movie from avi file type and was given two succeeding messages in the player before it closed. First it said something like I needed an additional codec then it said something like redirecting to microsoft codec something and that it was going to close - and then it did.

Well, I remembered something another user told me about on this forum a few days ago (thought the discussion was about something else to begin with). They said that most codec issues can be solved by downloading ubuntu-restriced-extras so I went into synaptic package manager to look for it and download it.

Well, I'm not very familiar with synaptic package manager; and, since I know the code for downloading apps and didn't want to fiddle with finding what to click in synaptic, I opened a terminal and typed: 'sudo apt-get install ubuntu-restricted-extras'. Everything seemed to go fine until I was presented with a gui window inside the terminal talking about accepting the licence agreement (restricted extras is a microsoft thing I guess).

Well there was no way to do anything with it so I just closed the terminal window thinking I could go back to synaptic and get it that way. Synaptic then tells me, basically, that it can't start up or something like that because another program is running and I need to close that. Well I figured I could solve something like this by restarting - so I did.

Now, after restart, I try to run synaptic and am given an error message saying dpkg something something and I need to run some code to correct it. It gives me the code to run in the error message. I tried that but am told in terminal that there is no such command. I actually tried a couple variations with the dash/ dashes between two of the words since I know Linux is particular about case and formatting, etc. No luck. Now I'm stuck. Please help so I can watch my movie tonight.

Attachment show a photo of the error message synaptic gives me at this point I am at right now.

Thanks,
Jake

---

### Post by uRock on 2011-04-03
bump for move to proper sub-forum.

---

### Post by ClientAlive on 2011-04-03
Omg! I'm sorry. I thought I was in general help. That's what I though I clicked on. I don't know how to move it. I'm looking and I looked earlier regarding another thread. I'm sorry.

Jake

---

### Post by uRock on 2011-04-03
It was in general forums. I moved it here to hopefully gain the experience eyes that can help with your issue.:)

---

### Post by ClientAlive on 2011-04-03
Hi everyone,
 
I'm running Ubuntu 11.04, have mplayer and smplayer as the gui for it. I  was trying to watch a certain movie from avi file type and was given  two succeeding messages in the player before it closed. First it said  something like I needed an additional codec then it said something like  redirecting to microsoft codec something and that it was going to close -  and then it did.

Well, I remembered something another user told me about on this forum a  few days ago (thought the discussion was about something else to begin  with). They said that most codec issues can be solved by downloading  ubuntu-restriced-extras so I went into synaptic package manager to look  for it and download it.

Well, I'm not very familiar with synaptic package manager; and, since I  know the code for downloading apps and didn't want to fiddle with  finding what to click in synaptic, I opened a terminal and typed: 'sudo  apt-get install ubuntu-restricted-extras'. Everything seemed to go fine  until I was presented with a gui window inside the terminal talking  about accepting the licence agreement (restricted extras is a microsoft  thing I guess).

Well there was no way to do anything with it so I just closed the  terminal window thinking I could go back to synaptic and get it that  way. Synaptic then tells me, basically, that it can't start up or  something like that because another program is running and I need to  close that. Well I figured I could solve something like this by  restarting - so I did.

Now, after restart, I try to run synaptic and am given an error message  saying dpkg something something and I need to run some code to correct  it. It gives me the code to run in the error message. I tried that but  am told in terminal that there is no such command. I actually tried a  couple variations with the dash/ dashes between two of the words since I  know Linux is particular about case and formatting, etc. No luck. Now  I'm stuck. Please help so I can watch my movie tonight.

Attachment show a photo of the error message synaptic gives me at this point I am at right now.

Thanks,
Jake

---

### Post by matt_symes on 2011-04-03
Hi

> Well there was no way to do anything with it so I just closed the terminal window thinking I could go back to synaptic and get it that way. Synaptic then tells me, basically, that it can't start up or something like that because another program is running and I need to close that. Well I figured I could solve something like this by restarting - so I did.

Now, after restart, I try to run synaptic and am given an error message saying dpkg something something and I need to run some code to correct it. It gives me the code to run in the error message. I tried that but am told in terminal that there is no such command. I actually tried a couple variations with the dash/ dashes between two of the words since I know Linux is particular about case and formatting, etc. No luck. Now I'm stuck. Please help so I can watch my movie tonight

Open a terminal and type

```
sudo dpkg --configure -a
```

Enter your password It will not be echoed to the screen. This is normal.

On the microsoft EULA page hit the tab key to move to OK and the hit enter. Tab to move. Enter to select.

Kind regards

---

### Post by ClientAlive on 2011-04-03
Oh Wow! I got confused. Didn't understand what you were saying - I thought you were saying I put it in the wrong place to begin with and then when I looked at the string at the top of the and saw where it was at I thought I made a mistake and put it there and that, that was the wrong place. Now I've gone and re-posted in general help and come back here and marked as solved. I'm such an idiot.

Don't know what the heck to do now. Guess I may not get to watch this movie tonight. It'd be a shame. Lol

Thanks, and sorry for the confusion.

Jake

--------------------------

Found the "unsolved" link and did that. I'm just gonna leave it alone n' see what happens here. Good grief! I'll get the hang of this yet tho.

Thx

---

### Post by ClientAlive on 2011-04-03
Thanks matt, 

But the result I get in terminal does not seem to indicate I've made any progress.

The following is the content of the terminal window after entering what you said:

clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ sudo dpkg-configure -a[sudo] password for clientalive: 
sudo: dpkg-configure: command not found
clientalive@clientalive-HP-Pavilion-ze2000-PV336AV-ABA:~$ 

Thanks again.

Jake
-------------------

Also: Just tried restarting synaptic and get the same error message.

---

### Post by Anduu on 2011-04-03
The command is:
```
sudo dpkg --configure -a
```

Try copy and pasting...

Hopefully you will get the EULA again.

When one of those interactive terminal windows opens make sure it has focus and then you can navigate them using your Tab and arrow keys.

---

### Post by Rasa1111 on 2011-04-03
Hi Jake,

 With restricted extras,
If you do not 'finish' it, by accepting the user agreement, 
It will not properly install/work. 

When done through terminal,
there is a way to accept/select "yes" , But I have only managed to get it installed once or twice that way..
 I do recall a few times not being able to get away from the "do you accept" screen in terminal.

So, As I did..
You could just go to ubuntu software center, find restricted extras,
and install it from there. You will also be given a user agreement window/check box when it is finished, but you can simply check 
"yes/i agree", and let it proceed without any hangups. 

That's about all I can think of right now. 
Should work fine though. 

Also,
 You may want to check out VLC Player.
VLC comes with pretty much most of the codecs as it is.
So just having that by itself, even without restricted extras, would still allow you to play most files you have.

So even if you just install VLC, you should be able to watch your movie tonight. ;)
Good luck, have fun.

@ Anduu~ good tip! thanks!  :D

---

### Post by matt_symes on 2011-04-03
Hi

DOH. Typo. Follow my #2 post but use

```
sudo dpkg --configure -a
```

I will edit my earlier post.  Wow what a thread.

Kind regards

---

### Post by howefield on 2011-04-03
Threads merged.

No need for duplicates. :)

---

### Post by ClientAlive on 2011-04-03
Anduu:

That seemed to have worked as I did get something to happen in terminal. I tried to then go get the app through software center and after hitting the "install" button am given another error message. I don't understand what is going on here but I can see not getting this fixed may be a bigger issue for me than just not getting to watch some movie.

Attached is the picture of the error message I got last (as described above).

Thanks.

Jake

---

### Post by Anduu on 2011-04-03
> **ClientAlive said:**
> Anduu:

That seemed to have worked as I did get something to happen in terminal. I tried to then go get the app through software center and after hitting the "install" button am given another error message. I don't understand what is going on here but I can see not getting this fixed may be a bigger issue for me than just not getting to watch some movie.

Attached is the picture of the error message I got last (as described above).

Thanks.

Jake

Make sure all package managers are closed and try:
```
sudo apt-get -f install
```
and see what that spits out.

---

### Post by ClientAlive on 2011-04-03
I think I got it brother. What you had me run seemed like it sort of restarted the install. I made a mistake by not selecting "yes" and leaving it on the default "no" when the time came. Did some more fiddling around in the terminal and in the end it looks like it is installed based on what software center says (its listed as an installed app). I'm gonna go ahead and mark this one as solved for now.

Thanks so much for your help - all of you.

Sincerely,
Jake

---

### Post by Anduu on 2011-04-03
> **ClientAlive said:**
> I think I got it brother. What you had me run seemed like it sort of restarted the install. I made a mistake by not selecting "yes" and leaving it on the default "no" when the time came. Did some more fiddling around in the terminal and in the end it looks like it is installed based on what software center says (its listed as an installed app). I'm gonna go ahead and mark this one as solved for now.

Thanks so much for your help - all of you.

Sincerely,
Jake

Cheers :)

---

### Post by ClientAlive on 2011-04-03
I suppose I will read about this sooner or later but I'm kind of curious about one last thing:

does the "-f " in that string of code you shared with me stand for "finish" or something like that?

It's ok if it's too complicated to get into. Just wondering since what I saw happen when I ran it.

thx

Jake

---

### Post by Anduu on 2011-04-03
> **ClientAlive said:**
> I suppose I will read about this sooner or later but I'm kind of curious about one last thing:

does the "-f " in that string of code you shared with me stand for "finish" or something like that?

It's ok if it's too complicated to get into. Just wondering since what I saw happen when I ran it.

thx

Jake
Pretty much any command you add --help to will give a list of options

```
apt-get --help
Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  [COLOR="Red"]-f  Attempt to correct a system with broken dependencies in place[/COLOR]
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
```

---

### Post by matt_symes on 2011-04-03
Hi

It stands for fix broken

From man apt-get

```
-f, --fix-broken
Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. If
packages are specified, these have to completely correct the problem. The option is sometimes necessary when running APT for the first time; APT itself does not allow broken package
dependencies to exist on a system. It is possible that a system's dependency structure can be so corrupt as to require manual intervention (which usually means using dselect(1) or
dpkg --remove to eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken.
```

I'm glad it's fixed. Enjoy your movie :)

Kind regards

---

### Post by ClientAlive on 2011-04-03
Wow! Very interesting! You know (and not that doing this really matters) but intuitively it seems there is an easy way to get around actually accepting the eula and still end up with the installation. Something about intentionally using this fact about apt not allowing broken packages (and the fact that I think I ended up with that app from earlier installed and technically had never selected "yes" to the eula). In my case, earlier, it was an accident - but I can see how it can probably be done intentionally. Interesting stuff. I wonder if I just caught sight of a simple crack?

Thanks guys.

Jake

---

### Post by cariboo on 2011-04-03
You don't have to accept the EULA, the only thing that will happen, is that the mscorefonts won't get installed. The problem you ran into is because you stopped the install process before it was finished.

---

### Post by ClientAlive on 2011-04-19
> Also, You may want to check out VLC Player.
VLC comes with pretty much most of the codecs as it is.
So just having that by itself, even without restricted extras, would still allow you to play most files you have.

So even if you just install VLC, you should be able to watch your movie tonight. :wink:
Good luck, have fun.

@ Anduu~ good tip! thanks!  :grin:

Was just looking over some of my old threads to see if I missed anyone or anything I should have said.

Ultimately I did end up switching to VLC but it wasn't until a few days later, after getting the other one working. I used to use VLC under Windows when I was running XP so I know that it is a great piece of software. Switching back to it is one of the best decisions I've made. Works flawlessly on everything I need it for. Easy to use, all that.

Thanks guys.

Jake

---

### Post by beew on 2011-04-19
> **ClientAlive said:**
> Was just looking over some of my old threads to see if I missed anyone or anything I should have said.

Ultimately I did end up switching to VLC but it wasn't until a few days later, after getting the other one working. I used to use VLC under Windows when I was running XP so I know that it is a great piece of software. Switching back to it is one of the best decisions I've made. Works flawlessly on everything I need it for. Easy to use, all that.

Thanks guys.

Jake

It is funny, whether VLC or mplayer works better seems to depend on the hardware. Also mplayer performance varies depending on the build. 

I am on an hp pavallian dv2 netbook right now (with the adm/ati open source graphic driver). This is not a very strong machine and with the open source driver so not surprising that vlc doesn't work too great on some 720p mp4 movies. But with mplayer it is interesting.

Installed versio fromn the MOTU ppa and it was ok but not great, it stuttered and dropped frames for some fast action scenes. But then I installed the svn version from the mplayer-coreavc ppa (I don't use coreavc, but it is an excellent mplayer build statically linked to updated version of ffmpeg) and now it works great, playback is smooth even for some fast action clips that previously were not watchable with mplayer and vlc.

I am not sure if VLC performance would be improved with updated versions of ffmpeg/libav but ppa for those are not ready for Natty yet (packages have dependency conflicts if try to install)

P.S. I am not sure if VLC is still single cored. ffmpeg-mt has been merged to the main library in March but it may take a while for the change to filter down to VLC.

---

