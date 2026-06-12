---
title: "Can't get remote to work in Myth. Hauppauge PVR-250 (Fiesty)"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by Rictus on 2007-04-27
I've done all the tutorials. When I check in a terminal with irw it works fine, but when I switch to Myth...nothing. I have lircrc all set up and made sure all the commands were spelled the same.
The only thing I'm not sure about is where the lircrc file goes. I put it in ~/.mythtv/lircrc like it says in the tutorial. But it also talkes about a symbolic link. I talks like this isn't nescarry if I use the standalone method, which is what I think I did. 
Something isn't getting through though.
Thanks,
Rick

---

### Post by newlinux on 2007-04-27
Hmm, for standalone you have put it in the right place. I know you probably have it right from what you mentioned, but for sanity's sake it might help to post your lircd.conf and your ~/.mythtv/lircrc file.
You also might want to try and see if you can get lirc to work with any other applications (like mplayer, or maybe try a quick example with irexec) to see if somehow it is myth specific. For this, you'd want to create an ~/.lircrc file.

---

### Post by Rictus on 2007-04-27
Well, it's a server so I have no way of cutting and pasting (that I know of) to the internet.
I'm going to try and fix my other computer's Ubuntu install and see if I can remotely log on.

---

### Post by newlinux on 2007-04-27
just ftp the files over to whatever OS you are posting from is one of many ways... File sharing, ssh in (using putty if you are on windows), etc. Or you could just add a lightweight window manager to you server. since all of my servers are connected to displays, I always make sure I can start a window manager... Just because it's a server doesn't mean it doesn't have a display.

---

### Post by Rictus on 2007-04-28
Don't know how to do any of that but I followed these, my lircrc looks exactly like the top portion of this page: 
[http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt](http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt) 
and the 3rd section of this, (which I modified the names to match the lircrc file)
[http://lirc.sourceforge.net/remotes/hauppauge/lircd.conf.hauppauge](http://lirc.sourceforge.net/remotes/hauppauge/lircd.conf.hauppauge)


Well I tried putting conf file back to it's original state and modified the button names in the lircrc file in the off chance that had something to do with it. 
That didn't help.
Then I ran the code for the sybolic link,  ln -s ~/.lircrc ~/.mythtv/lircrc, 
and that seemed to do nothing. 
I oviously have something messed up here but I cannot see what.
Maybe if I could figure out how to copy the files from the terminal in my mythbox over to this machine I could post my files.

---

### Post by Rictus on 2007-04-28
The only thing I can come up with is ~/.lircrc folder doesn't have anything in it. Does it have to?
The ~/.mythtv.lircrc has my lircrc file in it. Like I said in my edit above I ran the code to make a symbolic link like it says here:
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)
but still doesn't work in myth.
If this is the problem how do I fix it?
Thanks,
Rick

---

### Post by newlinux on 2007-04-28
> **Rictus said:**
> The only thing I can come up with is ~/.lircrc folder doesn't have anything in it. Does it have to?
The ~/.mythtv.lircrc has my lircrc file in it. Like I said in my edit above I ran the code to make a symbolic link like it says here:
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)
but still doesn't work in myth.
If this is the problem how do I fix it?
Thanks,
Rick

I assume you mean ~/.mythtv/lircrc not /.mythtv.lircrc. If not, that could be the problem

The command for the tutorial assumes the file was first created in ~/.lircrc, not in ~/.mythtv/lircrc. Since I think you created the standalone file in ~/.mythtv/lircrc first you can do the following:

make sure ~/.mythtv/lircrc contains your LIRC mappings.
make sure ~/.lircrc doesn't exist already exist. If it does, delete it. Then type
```

ln -s ~/.mythtv/lircrc ~/.lircrc
```

This will link ~/.lircrc to ~/.mythv/lircrc. The command in the tutorial links ~/.mythtv/lircrc to ~/.lircrc.


So when you are done, you should be able to do 
```

cat ~/.lircrc 
```

```
cat ~/.mythtv/lircrc

```

and view the same file.
That .lircrc file you posted has bindings for mplayer and xine. After properly linking the files test it in those applications as well and post back what happens.

---

### Post by newlinux on 2007-04-28
You can install putty for windows to ssh into your ubuntu machine:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)
It's pretty quick.

You can also install a few different Xservers if you want to be able to open X programs from your Ubuntu machine on your windows machine. i use Xming because it is pretty portable:

[http://sourceforge.net/project/showfiles.php?group_id=156984](http://sourceforge.net/project/showfiles.php?group_id=156984)


Make sure first on your server machine you install openssh-server
```

sudo apt-get install openssh-server

```

---

### Post by tranquillion on 2007-04-28
> **Rictus said:**
> The only thing I can come up with is ~/.lircrc folder doesn't have anything in it. Does it have to?


You should not have a ~/.lircrc folder.  Grab the lircrc-haupgrey-g3.txt file, and save it with the file name ~/.lircrc.  Then you can make the symlink to ~/.mythtv/lircrc with
```
ln -s ~/.lircrc ~/.mythtv/lirc
```
You can verify that it's set up correctly by typing
```
more ~/.mythtv/lirc
```
and making sure that this lists the mappings.

---

### Post by Rictus on 2007-04-28
OK I managed to get my dual boot comp install up and logged into my mythbox and copy and pasted my lircrc. Not sure how to post it in code window so sorry.


#MythTV LIRC Config
#

begin
prog =  mythtv
button = TV
repeat = 3
config = F5
end

brgin
prog = mythtv
button = Videos
repeat = 3
config = F2
end

# Not yet defined
begin
prog = mythtv
button = Music
repeat = 3
config = Up
end

# Given another function for now, not using  mythgallery???
begin
prog = mythtv
button = Pictures
repeat = 3
config = F
end

begin
prog = mythtv
button = Guide
repeat = 3
config = F3
end

# ToDo list, myth has no radio function
begin
prog = mythtv
button = Radio
repeat = 3
config = F4
end

begin
prog = mythtv
button = Up
repeat = 3
config = Up
end

begin
prog = mythtv
button = Down
repeat = 3
config = Down
end

begin
prog = mythtv
button = Left
repeat = 3
config = Left
end

begin
prog = mythtv
button = Right
repeat = 3
config = Right
end

# Channel Up
begin
prog = mythtv
button = Ch+
repeat = 3
config = Up
end

# Channel down
begin
prog = mythtv
button = Ch-
repeat = 3
config = Down
end

# OK/Select
begin
prog = mythtv
button = OK
config = Space
end

# Play
begin
prog = mythtv
button = Play
config = Return
end

# Stop
begin
prog = mythtv
button = Stop
config = I
end

# Esc/Exit/Back
begin
prog = mythtv
button = Back/Exit
config = Esc
end

# Power Off/Exit
begin
prog = mythtv
button = Power
config = Esc
end

# Pause
begin
prog = mythtv
button = Pause
repeat = 3
config = P
end

# Mute
begin
prog = mythtv
button = Mute
repeat = 3
config = |
end

# Fast Forward (30 sec. default)
begin
prog = mythtv
button = Rewind
repeat = 3
config = <
end

# Rewind (10 sec. default)
begin
prog = mythtv
button = Forward
repeat = 3
config = >
end

# Skip Forward (10 min. default)
begin
prog = mythtv
button = SkipForward
repeat = 3
config = End
end

# Skip backward (10 min. default)
begin
prog = mythtv
button = Replay/SkipBackward
repeat = 3
config = Home
end

# Record
begin
prog = mythtv
button = Record
repeat = 3
config = R
end

# Delete
begin
prog = mythtv
button = Red
repeat = 3
config = D
end

# Decrease play speed
begin
prog = mythtv
button = Green
repeat = 3
config = J
end

# Display EPG while in live TV
# View selected show while in EPG
begin
prog = mythtv
button = Menu/i
repeat = 3
config = M
end

# Scroll up
begin
prog = mythtv
button = Vol+
repeat = 3
F11
end

# Scroll down
begin
prog = mythtv
button = Vol-
repeat = 3
config = F10
end

# Bring up OSD info
begin
prog = mythtv
button = Go
repeat = 3
config = I
end

# Change display aspect ratio
begin
prog = mythtv
button = Prev.Ch
repeat = 3
config = W
end

# Double speed watch
begin
prog = mythtv
button = Yellow
repeat = 3
config = J
end

# Change tuners
begin
prog = mythtv
button = #
repeat = 3
config = Y
end

# Bring up time stretch
begin
prog = mythtv
button = Blue
repeat = 3
config = A
end

# Numbers 0-9
begin
prog = mythtv
button = 0
repeat = 3
config = 0
end

begin
prog = mythtv
button = 1
repeat = 3
config = 1
end

begin
prog = mythtv
button = 2
repeat = 3
config = 2
end

begin
prog = mythtv
button = 3
repeat = 3
config = 3
end

begin
prog = mythtv
button = 4
repeat = 3
config = 4
end

begin
prog = mythtv
button = 5
repeat = 3
config = 5
end

begin
prog = mythtv
button = 6
repeat = 3
config = 6
end

begin
prog = mythtv
button = 7
repeat = 3
config = 7
end

begin
prog = mythtv
button = 8
repaet = 3
config = 8
end

begin
prog = mythtv
button = 9
repeat = 3
config = 9
end

I definately think the problem has to do with ~/.lirc file.
"[COLOR="Red"]more ~/.mythtv/lirc[/COLOR]"   gives no such file or directory.
"[COLOR="Red"]cat ~/.lircrc[/COLOR]" and "[COLOR="Red"]cat ~/.mythtv/lircrc[/COLOR]" both give me the correct file from above though.???

I tried the "[COLOR="Red"]ln -s ~/.mythtv/lircrc ~/.lircrc[/COLOR]" command after deleting my ~/.lircrc file seems not to have worked.???

New edit: I tried to copy using sudo cp ~/.mythtv/lircrc to ~/.lircrc which returned "are the same file"

---

### Post by Rictus on 2007-04-29
Heres the result of dmesg | grep:

dmesg | grep lirc
[  47.840073] lirc_dev: IR Remote Control driver registered, at major 61
[  47.943376] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[  48.148124] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[  48.148464] lirc_dev: lirc_register_plugin: sample_rate: 10

Help any?

---

### Post by newlinux on 2007-04-29
> **Rictus said:**
> 
"[COLOR="Red"]cat ~/.lircrc[/COLOR]" and "[COLOR="Red"]cat ~/.mythtv/lircrc[/COLOR]" both give me the correct file from above though.???

I tried the "[COLOR="Red"]ln -s ~/.mythtv/lircrc ~/.lircrc[/COLOR]" command after deleting my ~/.lircrc file seems not to have worked.???

New edit: I tried to copy using sudo cp ~/.mythtv/lircrc to ~/.lircrc which returned "are the same file"


This means they are already properly linked. If you see the same file when you cat them then they are the same. you could also do ls -l in the directory and it will show you what a file is linked to.

> **Rictus said:**
> Heres the result of dmesg | grep:

dmesg | grep lirc
[  47.840073] lirc_dev: IR Remote Control driver registered, at major 61
[  47.943376] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[  48.148124] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[  48.148464] lirc_dev: lirc_register_plugin: sample_rate: 10

Help any?

This is most likely the problem... But I'm not sure how to fix it right now... I'll look around... Did you ever check if the remote works with mplayer?

---

### Post by newlinux on 2007-04-29
Maybe the bottom of this thread will help...
[http://ubuntuforums.org/showthread.php?t=383472](http://ubuntuforums.org/showthread.php?t=383472)

Are you using the on card IR blaster/receiver or the USB IR blaster/receiver?

what does ```
lsmod | grep lirc
``` return?

---

### Post by Rictus on 2007-04-30
newlinux, first of all I want to thank you for trying to help me. I 'm not real good at linux.
OK, so I only have a terminal when I'm not in mythtv so I don't have mplayer or xine (that I know of).
When you say thats most likely the problem, what do you see?
I begining to think this is somthing really simple because out of all the things I've tried my remote works fine with irw everytime.
So the backend seems to be working fine but Mythtv isn't getting the signal for some reason.
I'm not useing any kind of a blaster just a receiver. PVR-250 doesn't have the built in blaster. I have a combined frontend/backend box. No USB, just the card.
I have a final to study for for tuesday. I'll try ```
lsmod | grep lirc
``` when I get through with that.
(I figured out how to do the code blocks. :)

---

### Post by newlinux on 2007-04-30
You are welcome, although I haven't helped much yet :)

I thought:

[ 47.943376] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.

Might be the problem. If you are using the built in IR port than you are probably loading the right modules, and your LIRC files look good, and based on your previous post (the cat output) you have the files in all the necessary places.

It would be nice to know if other programs respond to LIRC. You can run mplayer from Mythtv through mythvideo (you can configure mythvideo to launch mplayer to play files). That way you can test mplayer and LIRC.

Maybe there is something I'm not getting. Could you describe your setup (do you have a separate frontend and backend machine, which machine has LIRC installed, how do you usually launch mythtv). I'm grasping at straws. But more info will perhaps help me help you, if not others out there who might see this thread.

---

### Post by Rictus on 2007-05-02
It's a combined frontend/backend. Myth logs in automatically as per the tutorial. I have to quit Myth to get to the terminal.

This command: 
```
lsmod | grep lirc
```returns the following:

```
lirc_i2c               11268  0 
lirc_dev               15988  1 lirc_i2c
i2c_core               22784  11 cx88xx,bttv,lirc_i2c,i2c_ec,msp3400,saa7115,tuner,ivtv,i2c_algo_bit,tveeprom,i2c_nforce2
```Any help?

---

### Post by Rictus on 2007-05-03
Here's my lircd.conf file if that's any help.

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2-CVS(default) on Sun Apr 22 08:10:32 2007
#
# contributed by
#
# brand:                       Hauppauge 250
# model no. of remote control: A415-HPG
# devices being controlled by this remote:PVR-250
#

begin remote

  name Hauppauge_250
  flags RC5|CONST_LENGTH
  bits           13
  eps            30
  aeps          100

  one             969     811
  zero            969     811
  plead         1097
  gap          114605
  toggle_bit     2

      begin codes
          Power                    0x00000000000017BD
          Go                       0x00000000000017BB
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Play                     0x00000000000017B5
          SkipForward              0x000000000000179E
          Replay/SkipBackward      0x00000000000017A4
          Rewind                   0x00000000000017B2
          Foeward                  0x00000000000017B4
          Pause                    0x00000000000017B0
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          0                        0x0000000000001780
          Asterix                  0x000000000000178A
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
```My wife is starting to give me that "I told you so " look. :(

---

### Post by newlinux on 2007-05-03
nothing jumps out from those commands. Try to see if mplayer responds to commands. You might want to try reinstalling LIRC.

---

### Post by Rictus on 2007-05-04
I got mplayer instlled and don't know how to run it from the command line, so I typed in mplayer D:. It showed about 3 typos in my lircrc file. I corrected those, but it didn't help. I don't know how to start mplayer from a terminal.

---

### Post by newlinux on 2007-05-06
When you log in and use mythtv do you log in as mythtv or some other user? Is it the same user you are when you have been typing in the commands (like the linking of the files. If you run mythtv as user mythtv, then the lircrc file needs to be in /home/mythtv/.mythtv/lircrc. If you run myth as some other user it needs to be in /home/OTHERUSER/.mythtv/lircrc. Similarly the link should be in /home/mythtv/.lircrc or /home/OTHERUSER/.lircrc. When you use ~/ it defaults to the home dir of the user logged in. So if you log in to configure LIRC as a different user than you run mythtv as, this is your problem.

I'm grasping at straws here. Sorry I haven't been more helpful.

---

### Post by Rictus on 2007-05-06
OK I got impatient and made another post but jimp180 said to copy the lircrc file to different places. This would makes sense.
[http://ubuntuforums.org/showthread.php?p=2605367#post2605367](http://ubuntuforums.org/showthread.php?p=2605367#post2605367)
 
I'm thinking that per the tutorial I must be getting into myth by login: mythtv. (It is set to auto load so I don't actually see the login).
But at the terminal (which is the same as the backend login I assume) it says
rick@ubuntumyth:~$
 
So should I just copy the files to other areas like jimp180 says? If so what would the user be rick or ubuntumyth?

---

### Post by newlinux on 2007-05-06
Yep, that is the problem. You are putting the configuration files for /home/rick. If you are running mythtv as the mythtv user you need to put the file in ~/home/mythtv/.mythtv/lircrc
If you are logged in as "rick":

```

sudo -u mythtv cp /home/rick/.mythtv/lircrc /home/mythtv/.mythtv/lircrc

```

Sorry I didn't catch this earlier. I usually run mythtv as my primary user, not as the mythtv user... (cause I use it as a regular desktop as well).

---

### Post by Rictus on 2007-05-07
OMG!!!!!! It works!! yes yes yes.:-D That was it.
 
I'm so happy now. I ran upstairs jumping.
 
Thank you so much. I began to think it was something silly because irw always worked properly. (bows to newlinux)
 
Thats what keeps ubuntu alive is the community. People willing to take time to help others. Some quit, but when you finally get to the end, the reward is great.

---

### Post by newlinux on 2007-05-07
Glad this worked. So simple, I could have saved you a lot of tiem if I just paid better attention. Happy mything and ubuntuing...

---

