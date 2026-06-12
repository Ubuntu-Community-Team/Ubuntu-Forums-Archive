---
title: "[SOLVED] Newbie confused about how to configure PVR-350 remote!"
date: 2007-11-24
forum: Mythbuntu
---

### Post by wilberfan on 2007-11-24
I'm VERY new at mythbuntu, and have finally got it (mostly) working.  I can watch TV and videos...I haven't tried recording anything yet.

My remote IS working--but not very accurately.

Some of the buttons work the way they're labeled--"guide", "up", "down", "left", right", "ok" , "Volume Up", "Volume Down"....etc...

But others are problematic:  If I want to change channels, I can't just press "Channel Up or Down"--because that triggers "jump back" or "jump ahead".  To change the channel, I have to press "guide", then up or down to the channel I want, then "menu/i" to select that channel!

I copied the PVR-350 section of [this file]("http://lirc.sourceforge.net/remotes/hauppauge/lircd.conf.hauppauge") and replaced whatever was in my /etc/lirc/lircd.conf file.

I then tested all of the buttons using the "irw" command--and they all matched perfectly (ie, produced all the numbers listed in the lircd.conf file.

I then ran a "sudo /etc/init.d/lirc restart.

No change.   I would have bet money that would have fixed it, too...  

What's the secret to getting the buttons to perform their proper functions?   :confused:

---

### Post by wilberfan on 2007-11-24
Can anyone see what might be amiss here?    (And while I'm at it, why is there *four* .lircrc files??  Am I supposed to change ALL of them to fix the functioning of the buttons that aren't working properly??)  

home/mythtv/.lircrc
home/mythtv/.mythtv/lircrc
home/wilberfan/.lircrc
home/wilberfan/.mythtv/lircrc

:confused:

```
begin
    remote = Hauppauge_350
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = SkipForward
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Replay/SkipBackward
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Menu/i
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Ch-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Back/Exit
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Ch+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Vol-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Vol+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end
```

Here's my lircd.conf

```
#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R www.mythtvportal.com
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
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
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remot
```e

---

### Post by uopjohnson on 2007-11-25
I wouldn't mess with your lircd.conf file.  The one that some with mythbuntu seems to work really well for the 350 remote.  What you are concerned about is your lircrc file.  There are four of these because every user gets one in their home director and myth installs its own in every home directory in case you are using your remote with multiple programs.  I would do this:
1) Figure out which user the frontend is running as.  In other words who is logged into the machine when the frontend is started.
2) become that user ```
sudo su - USER
```
3) change to the users home direcory
```
cd
```
4) Delete the myth specific .lircrc file
```
cp ~/.mythtv/lircrc ~/.mythtv/lircrc-bak
rm ~/.mythtv/lircrc

```
5) Link the myth file to your users lircrc
```
ln -s ~/.lircrc mythtv/lircrc
```
6) Edit your ~/.lircrc file to have the right button configuration.

Step 6 involves two things, first figure out what button you want to effect, then decide how it should work.  The easiest way to do this is with irw.  Press the button on the remote, then edit the .lircrc file find that button and change the config = FOO line to config = BAR where BAR is the key on yoru keyboard you want lirc to press for you.  For instance for volume up it would be ].

---

### Post by superm1 on 2007-11-25
Also, i'll interject a few comments here.  The ones in /home/mythtv are not used for anything.  They were merely there for legacy purposes if someone was to try to use ubuntu-mythtv-frontend.

The reason for the different one in ~/.mythtv/lircrc and ~/.lircrc is because the one in ~/.mythtv/lircrc is only for mythtv whereas the one in ~/.lircrc is for multiple other apps.

If your issues are only in mythtv, then you just need to modify the one in ~/.mythtv/lircrc, but doing the symbolic link should work out as well, just modify ~/.lircrc

---

### Post by wilberfan on 2007-11-25
VERY useful advice!  For example, I had no idea that you had to configure the commands using the equivalent *keyboard* shortcut...  (ie, "U" to increase play speed, "/" to jump to the next favorite channel, etc)

I'll have to go in search of those and see if I can make any progress...

I'm VERY impressed with Mythbuntu, so far...

Thanks for your help so far!  :)

---

### Post by foxbuntu on 2007-11-25
I have built a test deb with updates for this problem. please try installing this version and report back on any problem incurred with it. Just download it and save it to /usr/src

```
sudo dpkg -i mythbuntu-lirc-generator_0.16-0ubuntu1+foxbuntu1_all.deb
```

---

### Post by foxbuntu on 2007-11-25
Actually this file can be saved any where and then use the above code to install it.

---

### Post by wilberfan on 2007-11-25
VERY cool, but I got the following when I installed it:

> (Reading database ... 74080 files and directories currently installed.)
Preparing to replace mythbuntu-lirc-generator 0.16-0ubuntu1 (using mythbuntu-lirc-generator_0.16-0ubuntu1+foxbuntu1_all.deb) ...
Unpacking replacement mythbuntu-lirc-generator ...
Setting up mythbuntu-lirc-generator (0.16-0ubuntu1+foxbuntu1) ...
Compiling /usr/lib/python2.5/site-packages/MythbuntuLircGenerator/mythtvhandler.py ...
  File "/usr/lib/python2.5/site-packages/MythbuntuLircGenerator/mythtvhandler.py", line 48
    "exit":"Escape", \ #Fix for bug 161875, however this may conflict on other issues. Remapping exit to back/exit, esc, ect.
                                                                                                                            
^
SyntaxError: unexpected character after line continuation character

pycentral: pycentral pkginstall: error byte-compiling files (12)
pycentral pkginstall: error byte-compiling files (12)
dpkg: error processing mythbuntu-lirc-generator (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythbuntu-lirc-generator

---

### Post by wilberfan on 2007-11-25
I dragged my mouse and keyboard into the next room (where the TV is!) and played with the keyboard shortcuts.

I found it odd that to change the channel I had to hit the up or down arrow key and then hit enter.   

Is that normal?    Would that have anything to do with why the channel up and down on the remote doesn't work properly?  (The remote goes into skip forward or back when I press the channel button.)

Maybe this is for another thread, but is there a way to set up the video out so that only the mythtv stuff goes to it, and all other "computer" functions (desktop, menus, terminal windows, firefox, etc) goes to my computer LCD?   

I have xfce installed, and have two screens configured in xorg...but if I start firefox, it opens on the TV!  I can't seem to drag it to my LCD, so I have to drag the keyboard and mouse into the den (and it's hell to read some of the fonts on my TV screen..)

---

### Post by uopjohnson on 2007-11-25
I'm preety sure you can use xinerama or something similiar to launch different apps on difernt screens. Not my area of expertise.  
To change the chanel up and then enter behavior you should go to setup -> TV Settings -> Playback 8 or 9 screens in there is a check box for browse mode.

---

### Post by wilberfan on 2007-11-25
> **uopjohnson said:**
> .  
To change the chanel up and then enter behavior you should go to setup -> TV Settings -> Playback 8 or 9 screens in there is a check box for browse mode.

Hmm.  That was already enabled...  :confused:

---

### Post by uopjohnson on 2007-11-25
When it is enabled you will have the press enter behavior.  Disable it and channel changes will be automatic.

---

### Post by wilberfan on 2007-11-25
> **uopjohnson said:**
> When it is enabled you will have the press enter behavior.  Disable it and channel changes will be automatic.

Excellent!   (Now I have to figure out how to get the channel up and down to work on the remote...)

---

### Post by foxbuntu on 2007-11-25
> **wilberfan said:**
> I dragged my mouse and keyboard into the next room (where the TV is!) and played with the keyboard shortcuts.

I found it odd that to change the channel I had to hit the up or down arrow key and then hit enter.   

Is that normal?    Would that have anything to do with why the channel up and down on the remote doesn't work properly?  (The remote goes into skip forward or back when I press the channel button.)

Maybe this is for another thread, but is there a way to set up the video out so that only the mythtv stuff goes to it, and all other "computer" functions (desktop, menus, terminal windows, firefox, etc) goes to my computer LCD?   

I have xfce installed, and have two screens configured in xorg...but if I start firefox, it opens on the TV!  I can't seem to drag it to my LCD, so I have to drag the keyboard and mouse into the den (and it's hell to read some of the fonts on my TV screen..)

This is the normal operation for MythTV. I have resolved the build issue with the package. Please download, install and rerun it.

```
$ mythbuntu-lircrc-generator
```

Make sure to NOT run it as sudo. Then you can restart lirc

```
sudo /etc/init.d/lirc restart
```

Then restart mythfrontend to make the changes take effect.

---

### Post by wilberfan on 2007-11-25
Awesome.

My channel up and down now behave as advertised!

:guitar:

---

### Post by foxbuntu on 2007-11-25
Great. Thanks from the prompt feedback.

---

### Post by curtvan on 2007-11-27
I just stumbled upon this thread and have the same issue. I downloaded and installed the updated mythbuntu-lircrc-generator but still my channel up/down do not work. When I run irw, everything matches the lircd.conf. Any other ideas?
Thanks

---

### Post by superm1 on 2007-11-27
> **curtvan said:**
> I just stumbled upon this thread and have the same issue. I downloaded and installed the updated mythbuntu-lircrc-generator but still my channel up/down do not work. When I run irw, everything matches the lircd.conf. Any other ideas?
Thanks
Regenerated the "dynamic" mappings in mcc.

---

### Post by curtvan on 2007-11-28
That did it.  Thank you.

---

### Post by arjay1 on 2007-12-06
> **foxbuntu said:**
> I have built a test deb with updates for this problem. please try installing this version and report back on any problem incurred with it. Just download it and save it to /usr/src

```
sudo dpkg -i mythbuntu-lirc-generator_0.16-0ubuntu1+foxbuntu1_all.deb
```

Sorry to be so thick but how do i download this file?  Left clicking on it does nothing and rightclicking on it doesn't offer a "save/dowload" function or anything similar?

RJ

PS - also will this work with a pvr150 remote (newer grey/black) model?

---

### Post by uopjohnson on 2007-12-06
I don't believe you need to download the file any more.  Just update your system.

---

### Post by superm1 on 2007-12-06
> **arjay1 said:**
> Sorry to be so thick but how do i download this file?  Left clicking on it does nothing and rightclicking on it doesn't offer a "save/dowload" function or anything similar?

RJ

PS - also will this work with a pvr150 remote (newer grey/black) model?
It will work with any remote.  It's now in gutsy-backports, make sure that you have gutsy-backports in your software sources list, and you should be offered to upgrade.

---

### Post by arjay1 on 2007-12-06
Thanks guys - you were on the button.

Actually, I had backports enabled already and the file had updated.  But, of course, you have to run it to get the new lirc!  I naturally thought the posted file was newer and better - never thought to run the one already on my machine.

Now if only I could get the rest of the buttons to work on my remote (only half do).

Have posted elsewhere but nothing as yet.

Tanks again

RJ

---

### Post by superm1 on 2007-12-06
> **arjay1 said:**
> Thanks guys - you were on the button.

Actually, I had backports enabled already and the file had updated.  But, of course, you have to run it to get the new lirc!  I naturally thought the posted file was newer and better - never thought to run the one already on my machine.

Now if only I could get the rest of the buttons to work on my remote (only half do).

Have posted elsewhere but nothing as yet.

Tanks again

RJ
Interesting to hear *more* buttons don't work.  That was the exact reason for that update, to get better pvr-350 support and more buttons working.

---

### Post by arjay1 on 2007-12-06
superm1 - the buttons that don't work are those like TV, TV guide pictures, video, radio, etc round the top of the remote and the four coloured ones along the bottom.  However, at least you have helped to get the main ones working - the pvr stuff in the middle.

More power to your elbow - I think you guys have done a fantasatic job.  Wish i could contribute on the programming side but it's not my field at all.

If it was, I would spend many a sleepless night, believe me, ripping apart mythmusic which has to be one of the weakest parts of the mythtv series by far.  Not that it doesn't work - it is just so un-intuitive and complex to understand - dreadful really...

Never mind: I can now record and watch tv shows using my remote - that's the main thing.

RJ

---

### Post by superm1 on 2007-12-06
> **arjay1 said:**
> superm1 - the buttons that don't work are those like TV, TV guide pictures, video, radio, etc round the top of the remote and the four coloured ones along the bottom.  However, at least you have helped to get the main ones working - the pvr stuff in the middle.

More power to your elbow - I think you guys have done a fantasatic job.  Wish i could contribute on the programming side but it's not my field at all.

If it was, I would spend many a sleepless night, believe me, ripping apart mythmusic which has to be one of the weakest parts of the mythtv series by far.  Not that it doesn't work - it is just so un-intuitive and complex to understand - dreadful really...

Never mind: I can now record and watch tv shows using my remote - that's the main thing.

RJ
Ah yeah, those buttons don't have support right now for any remotes atm.  If you'd like to help out, it doesn't have to be programming.

1) can you file a bug against mythbuntu-lirc-generator to remind us to get to those?

2) Try to frequent the forums when you've got time and know how for solving problems you see, the more people helping each other here, the better (and more time for us to focus on the programming side of things :))

---

### Post by arjay1 on 2007-12-07
superm1

Ok - I'll have to find out how to file a bug report - leave it to me.

As to helping in the forums - I do whenever I can, but most peope seem to have the same problems as me!!

Richard

EDIT: BTW - the non-PVR buttons work in GBPVR, Mediaportal and Win MCE - can't we nick something from them?

---

### Post by arjay1 on 2007-12-08
superm1 - a slight problem has arisen since I ran the lirc generator program.

My remote now works much better, but lirc no longer seems to autoload.  I have to run /etc/init.d/lirc start after any reboot of the system.

I seem to remember in earlier days we used to add some extra lines to rc local or /etc/modules or somewhere to have lirc autoload.  I expect that it is actually already in your script?  How do i check its location, autoload instructions, or whatever to get it loading at boot time?

Thanks for a very useful bit of automation...

RJ

---

### Post by superm1 on 2007-12-08
Try typing this:

```
sudo update-rc.d lirc defaults
```
That will make sure the lirc init script is ran at startup.

---

### Post by arjay1 on 2007-12-08
Wow - fast reply or what!  Thanks I'll give it a try and post back.

Richard

---

### Post by arjay1 on 2007-12-08
> **superm1 said:**
> Try typing this:

```
sudo update-rc.d lirc defaults
```
That will make sure the lirc init script is ran at startup.

OK - ran this but it just says something to the effect: system startup links for /etc/init.d/lirc already exist?  I rebooted but the remote still won't work without a /etc/init.d/lirc start

RJ

---

### Post by arjay1 on 2007-12-10
Hope it is OK to bump this.

Superm1 - are you still monitoring this thread, or should I start a new one?  My question is a bit away from the original topic?

RJ

---

### Post by superm1 on 2007-12-10
> **arjay1 said:**
> Hope it is OK to bump this.

Superm1 - are you still monitoring this thread, or should I start a new one?  My question is a bit away from the original topic?

RJ
Start up a new thread i'd say.  I'm wary of what the causes of this are going to be yet though.

---

