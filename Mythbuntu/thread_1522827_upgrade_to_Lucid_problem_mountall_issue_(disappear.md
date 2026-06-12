---
title: "upgrade to Lucid problem: mountall issue? (disappearing capture card)"
date: 2010-07-02
forum: Mythbuntu
---

### Post by wayover13 on 2010-07-02
I've encountered what I consider to be one of the weirdest problems I've ever seen after an upgrade. This applies to a system that's been running mythbuntu for about 3 years, and that has been upgraded to new releases several times. I need to point out that ther system does work, so it's not as if I'm left with a dead computer or something. What I'll post about amounts to a minor inconvenience at the least, and likely represents some kind of bug introduced in the latest release of myhtbuntu (10.04). Also, this will be a continuation of discussion of an issue I posted about at [http://georgia.ubuntuforums.org/showthread.php?p=9536222#post9536222](http://georgia.ubuntuforums.org/showthread.php?p=9536222#post9536222) .

The problem I encountered on upgrading to Lucid was that the boot process would hang, awaiting input from me (key presses, "S" or "M") before it would continue. The system would hang because it was not finding certain disks listed in /etc/fstab. And it wasn't finding those disks because they're not supposed to be present most of the time (they're for back-ups--you can read more about the set up at the link I provided above).

Well, that was a bit of an incovenience: why should I have to be around to press keys to tell the system to proceed because it wasn't finding disks that are not supposed to be present most of the time? Doesn't make much sense to me. I gather, through some subsequent reading, that this all relates to the mountall utility now being used by Ubuntu.

Some other research indicated to me that a possible solution to the problem of the system hanging during boot, awaiting key presses from me, would be to append the nobootwait option to relevant entries in my /etc/fstab file. I tried that and, sure enough, the system no longer hung while booting, awaiting key presses from me. Great, I thought, I've found a simple solution. 

Turns out I was wrong, though. While that solution did stop the system from pausing/hanging during the boot process, it introduced an even worse problem: it caused an important hardware component on this machine to become disabled--one of my two capture cards.

I discovered the problem the day after I'd intorduced the nobootwait option into relevant entries in my /etc/fstab file. I went to watch a recording and disovered, to my astonishment, that the program had been recorded using the cheaper of my two capture cards. I checked the recording schedule and there were no other recordings to be made in that time slot, so there should be no reason for a recording to be made through that card (slight back-track: I've set up this system so that almost all recording is to be done through the better-quality capture card, while live TV is to be captured by the cheaper one).

To further diagnose the problem, I tuned into live TV--which, as expected, was being captured through the cheaper card. But when I brought up the menu and tried to switch inputs to see what was up with the better-quality card, it was absent. It wasn't even presented as a choice. So, effectively, my system only knew about one of my two capture cards--the cheap one.

I got a little worried at first but,a few years of computer trouble-shooting has indicated to me the importance of back-tracking changes. I thought, hmmm, what's the most recent change I've made to this system that could have caused one of my capture cards to disappear? In fact the only recent change--since the last successful recording made using the better-quality capture card--was the editing I'd done to /etc/fstab.

I really could not imagine how that would affect capture cards, so I initially tried a couple of cold reboots. After each one, the system still came up with only one capture card available--the cheap one. So, it was time to experriment with reverting the /etc/fstab file.

I removed the nobootwait options from relevant /etc/fstab entries and, guess what? The system came up with both capture cards available. I tried adding/subtracting the nobootwait option a couple of times to see whether this really could be the cause for the disappearing capture card, with the following results. Each time I'd boot the system with noboowait appended to relevant entries in /etc/fstab, the system would come up with only one working card (the cheap one). Each time I would remove the nobootwait option and would reboot, the system would come up with both cards available.

My conclusion? Appending nobootwait to entries in /etc/fstab can interefere with your systems detection and initialization of certain non-storage hardware--in my case, a capture card. Weird but true. So now I'm once again stuck with a system that hangs during boot, awaiting key presses before it will continue.

Input on this issue will be appreciated.

James

PS I realize that probably the best place to post and ask about this issue is at the launchpad thread I reference in the thread I linked to above. But I can't post there. Why? <beginrant>These idiots expect me, for the "priviledge" of posting about a bug in their OS, to make up a new password. For at least two years now, I've decided I won't make up any more passwords. I've had too many problems forgetting passwords and frustrations associated with that, and my memory is not getting any better with age. I have a set number of low, medium, and high security passwords, and I refuse to create any more. With the ones I have there are at least a limited number of possibilities, should I not recall the password for a given site on the first (second, third . . .) try. But now, for the priviledge of posting about bugs at the launchpad site, none of my passwords are suitable. No, to meet with their approval, my password has to be at least 8 characters long, and must have at least one upper-case letter and one number in it. Ok, what's next? It used to be six characters, then six characters with letter/number combinations. Are they going to start asking for ten-character passwords next? And are they going to stipulate next that, not only do they need to have at least one upper-case letter and a number, but at least one punctuation character as well? At the rate things are going, I think they may. Which means we're all going to have to start making up new passwords again. Which means thousands of newly-made passwords are going to be quickly forgotten. No thanks. I'm sticking with the passwords I have--I don't need more to forget, or to have to go through a longer series of trial-and-errors before getting the right password for a given site (which sometimes, of course, results in you getting locked out of the system because you've tried too many times). And this for a site where I might post, oh, what, once every 5 years or so? No. You just won't get any help from me in diagnosing the problem you've introduced. Idiots. </endrant>.

---

### Post by jlagrone on 2010-07-02
I think your two problems are unrelated. A lot of people have had problems because upstart has made booting, in general faster.  Normally this would be a good thing, but it means that mythbackend is started before some or all capture cards and perhaps other hardware is fully initialized.  Thus, myth doesn't see the capture card.  There are numerous fixes posted in the forum:

[http://ubuntuforums.org/showthread.php?t=1521029](http://ubuntuforums.org/showthread.php?t=1521029)

or 

[http://ubuntuforums.org/showthread.php?t=1345079](http://ubuntuforums.org/showthread.php?t=1345079)

Try booting with the nobootwait options and restarting mythbackend and see if your card reappears.  If it does, your problem should be solvable by one of the above links and allow you to still use the nobootwait option

---

### Post by wayover13 on 2010-07-03
Thanks for your response, jlagrone. It does seem, in fact, that the problem I'm seeing is the same as the one for which you've provided links. I tried the experiment you suggested and, sure enough, when I boot with the noobootwait option appended to relevant entries in my /etc/fstab file and the machine comes up with only one capture card, but I then restart mythbackend, I do end up with both cards detected and operational on the system.

<beginlameexcuse> It did occur to me previously that this might have to do with the system booting too quickly. But I decided that, since, on several occassions when the system had paused and I hit the needed key in quick succession, the system was booting pretty much as quickly as it was with the nobootwait option appended in /etc/fstab. So, I thought I'd already excluded that possibility, but the test you've suggested proves that I did not.</endlameexcuse>

I'll have a look at those threads for the resolution.

James

---

### Post by wayover13 on 2010-07-04
Unfortunately, neither of the solutions suggested at the second thread work for me (mythbackend refuses to start after applying the suggested edits). The solution suggested at the first thread, while seeming to be simpler, is beyond my computing acumen: I have no idea how to "throw in(to /etc/init/mythtv-backend.conf) a sleep command ahead of the starting of the backend to make it wait an additional minute." If anyone has a more specific description of how to do this, I would appreciate further pointers. But as it stands now it looks like I'm stuck with leaving nobootwait out of the problem entries in /etc/fstab and pressing keys during the boot process so the computer will finish booting.

James

---

### Post by ian dobson on 2010-07-04
Hi,

OK, to edit the mythtv-backend.conf file:-

1) Go to the terminal
2) Type sudo  nano /etc/init/mythtv-backend.conf
3) Edit the file so that it looks like this:-


```

# MythTV Backend service
description     "MythTV Backend"
author          "Matt Mossholder <matt@mossholder.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on runlevel [016]

#expect fork
respawn

pre-start script
        sleep 1;
end script

script
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script
```

4) When your finished with editing press control X to save the changes.

Note: the line sleep 1 causes the script to wait 1 second before starting myth-backend. Maybe try a higher value (30)

Regards
Ian Dobson

---

### Post by wayover13 on 2010-07-04
Thanks for your input, Ian. Actually the sudo nano part of this I know how to do quite well. It's the content of the file that I don't understand, and exactly where which element should be placed. I begin to understand something about this from your example, though. But before trying what you've suggested, I note that the content of my mythbackend.conf file looks a bit different from the one you've posted, so I just want to post the content of mine and to ask whether I can simply expect to substitute yours for mine. Here's what mine looks like: > # MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on starting shutdown

#expect fork
respawn

script
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend $ARGS
end script
Specifically, the differences are that yours specifies a number for the runlevel ([016]) for the stop section, while mine says "stop on starting shutdown." Additionally, yours lacks the lines > USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER" So, despite these differences--which I suspect may be particular to differing releases--is it ok simply to substitute the version you've posted in place of mine? Also, are you running Lucid?

Thanks,
James

---

### Post by wayover13 on 2010-07-04
I decided to just go ahead and try a hybrid of our two files. So I used my file, but inserted your sleep argument into it. It seems to work fine, after a little adjustment.

More specifically, I inserted > pre-start script
        sleep 1;
end script between the "respawn" and "script" lines in my file, just as you did in yours (though I did change "1" to something else, as suggested). Initially, I had "sleep 60" since, from reading [http://ubuntuforums.org/showthread.php?t=1521029](http://ubuntuforums.org/showthread.php?t=1521029) I gathered that a one-minute delay before starting mythbackend might be needed. But that gave an error message, since the fronted was starting before the backend and was unable, upon starting, to connect to the backend. So I changed it from "sleep 60" to "sleep 30." 

With that, I did **not** get an error message from the frontend stating that it was unable to connect to the backend. No, even with nobootwait appended to relevant entries in my /etc/fstab file, the "sleep 30" clause seems to have resolved my problem of mythbackend starting before both my capture cards are initialized (resulting in there being only one card present to Mythtv). So, the problems seem to be resolved now: I don't have to do any key presses during boot-up in order to get the system to continue, and both capture cards are present to Mythtv once it starts. Thanks for your help on this, Ian--and this "sleep" solution does seem to me much simpler and better than the one posted about at [http://ubuntuforums.org/showthread.php?t=1345079](http://ubuntuforums.org/showthread.php?t=1345079) .

James

PS I may try further reducing the "sleep XX" interval. Perhaps I could get by with a 20-second, or even 10-second delay? I can't say I really notice a big difference in the amount of time the system takes to fully boot into Mythtv with the "sleep 30" interval, but I might try some further experimentation. If I do, I'll post results in this thread.

---

### Post by ian dobson on 2010-07-04
Hi wayover13,

Why not just build a simple loop in your pre-script that just loops until the device file exists in the /dev file system. Something like:

pre-start script
    # wait for listen on port 80
    while ! -e /dev/dvb/adapter1; do
        sleep 1;
    done
end script

This will wait until the dvb adapter1 exists, checking every second.

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-07-04
Upgrading to auto-builds may resolve the issue as well. mythbackend now waits for udev to finish before starting

---

### Post by wayover13 on 2010-07-05
> **ian dobson said:**
> Hi wayover13,

Why not just build a simple loop in your pre-script that just loops until the device file exists in the /dev file system. Something like:

pre-start script
    # wait for listen on port 80
    while ! -e /dev/dvb/adapter1; do
        sleep 1;
    done
end script

This will wait until the dvb adapter1 exists, checking every second.
Interesting proposal, Ian. That looks a lot like the solution proposed at [http://ubuntuforums.org/showthread.php?t=1345079](http://ubuntuforums.org/showthread.php?t=1345079) , only a bit simpler, doesn't it? I have two capture cards, as I've mentioned, so your sample script wouldn't work as-is for me. What would the script need to look like if it were checking not just for one, but for two capture cards? Also, I don't know if this would have any effect, but my system creates special dev entries for these cards--/dev/BT878 and /dev/PVR150, which are actually symlinks to /dev/video0 and /dev/video1--since I want the two cards to be in a certain order of priority in the system. Given that, should a modified script along the lines of the one you've posted be expected to work?

[QUOTE=tgm4883] Upgrading to auto-builds may resolve the issue as well. mythbackend now waits for udev to finish before starting[/quote]
Glad to know they've fixed this. Using auto-builds sounds a bit too experimentalish to me. I upgraded to Lucid since it's an LTS release, and I'm hoping to stick with it for the remaining life of this machine--which should be less than 3 years from now. All the same, it's nice to know about auto-builds, about which I hadn't heard before.

Thanks,
James

---

### Post by ian dobson on 2010-07-05
> **wayover13 said:**
> Interesting proposal, Ian. That looks a lot like the solution proposed at [http://ubuntuforums.org/showthread.php?t=1345079](http://ubuntuforums.org/showthread.php?t=1345079) , only a bit simpler, doesn't it? I have two capture cards, as I've mentioned, so your sample script wouldn't work as-is for me. What would the script need to look like if it were checking not just for one, but for two capture cards? Also, I don't know if this would have any effect, but my system creates special dev entries for these cards--/dev/BT878 and /dev/PVR150, which are actually symlinks to /dev/video0 and /dev/video1--since I want the two cards to be in a certain order of priority in the system. Given that, should a modified script along the lines of the one you've posted be expected to work?


Glad to know they've fixed this. Using auto-builds sounds a bit too experimentalish to me. I upgraded to Lucid since it's an LTS release, and I'm hoping to stick with it for the remaining life of this machine--which should be less than 3 years from now. All the same, it's nice to know about auto-builds, about which I hadn't heard before.

Thanks,
James

Hi,

If you have two cards then just change the loop line to something like:-
while  [ ! -e /dev/BT878 && ! -e /dev/pvr150 ]; do

I'm not sure if the syntax is 100% correct, as I don't have access to my Linux systems at the moment (New Windows 7 laptop that doesn't like my network).

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-07-05
> **wayover13 said:**
> Interesting proposal, Ian. That looks a lot like the solution proposed at [http://ubuntuforums.org/showthread.php?t=1345079](http://ubuntuforums.org/showthread.php?t=1345079) , only a bit simpler, doesn't it? I have two capture cards, as I've mentioned, so your sample script wouldn't work as-is for me. What would the script need to look like if it were checking not just for one, but for two capture cards? Also, I don't know if this would have any effect, but my system creates special dev entries for these cards--/dev/BT878 and /dev/PVR150, which are actually symlinks to /dev/video0 and /dev/video1--since I want the two cards to be in a certain order of priority in the system. Given that, should a modified script along the lines of the one you've posted be expected to work?


Glad to know they've fixed this. Using auto-builds sounds a bit too experimentalish to me. I upgraded to Lucid since it's an LTS release, and I'm hoping to stick with it for the remaining life of this machine--which should be less than 3 years from now. All the same, it's nice to know about auto-builds, about which I hadn't heard before.

Thanks,
James

Hmm, not sure why auto builds sounds expermentalish to you ([http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)). It's built from the upstream fixes branch. Just FYI Lucid shipped with the 0.23 RC.

---

### Post by ian dobson on 2010-07-05
> **tgm4883 said:**
> Hmm, not sure why auto builds sounds expermentalish to you ([http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)). It's built from the upstream fixes branch. Just FYI Lucid shipped with the 0.23 RC.

So will auto-builds go over to 0.24 when it comes out? In that days of 0.22 I ran the VDPAU backport from JYA on my frontend and a plain 0.22 on my backend. I don't really want to end up with a version problem with the Frontend/Backend and I don't update my backend all that often.

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-07-05
> **ian dobson said:**
> So will auto-builds go over to 0.24 when it comes out? In that days of 0.22 I ran the VDPAU backport from JYA on my frontend and a plain 0.22 on my backend. I don't really want to end up with a version problem with the Frontend/Backend and I don't update my backend all that often.

Regards
Ian Dobson

Nope, thats not how auto-builds works. There actually is an auto-builds ppa for each version of mythtv (0.21, 0.22, 0.23, 0.24). 0.24 is currently built from trunk, and will eventually be 0.24. 0.23 is built from the 0.23 fixes branch. It will never be 0.24. 

When 0.24 comes out, the 0.23 PPA will stop being built. This means that if you are on the 0.23 PPA, that you will be able to update to the last build that was pushed to it, but you won't be upgraded to 0.24 automatically. The only way to upgrade to 0.24 at that point will be to do a reconfigure on mythbuntu-repos and manually select 0.24. Note that each release of Mythbuntu/Ubuntu only has 2 version of MythTV built for it. Whatever was released with the distro, plus the next version. (ie. Karmic has builds for 0.22 and 0.23, but will not get 0.24)

I've been tweaking how the webpage is worded for auto-builds to make this more clear. Any suggestions to how to make this better will be reviewed.

---

### Post by ian dobson on 2010-07-07
Hi tgm4883,

Maybe explain that there are several different auto builds (one per version) and that if you select to use a specific auto build version you will get all the updates for this version but you won't get upgraded to a new version (without doing a distribution upgrade or manually going over to a newer auto build).

The last time I read the auto build FAQ it sounded as if you would get the newest (not necesary just the version you selected).

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-07-07
> **ian dobson said:**
> Hi tgm4883,

Maybe explain that there are several different auto builds (one per version) and that if you select to use a specific auto build version you will get all the updates for this version but you won't get upgraded to a new version (without doing a distribution upgrade or manually going over to a newer auto build).

The last time I read the auto build FAQ it sounded as if you would get the newest (not necesary just the version you selected).

Regards
Ian Dobson

How is this addition.

> Selecting a version will only get you updates for that version, you will NEVER be automatically updated to the next version of MythTV UNLESS you manually reconfigure the auto builds package and select a different version. (ie. If you select 0.23, you will NEVER be automatically updated to 0.24 UNLESS you manually reconfigure the auto-builds package and select 0.24)

now found on [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by ian dobson on 2010-07-07
Hi tgm4883,

Thats very clear now for me (Englander gone Swiss since about 24years).

Regards
Ian Dobson

---

