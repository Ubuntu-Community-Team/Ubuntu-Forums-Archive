---
title: "Audio CDs Hang"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by nlvivar on 2007-04-14
So I'm having problems playing audio cds on my Dell E1505. CD-ROMs and DVDs read ok, but the system hangs if I try using Sound Juicer to play or rip+encode the CD. Also, if I try playing or ripping+encoding on Grip, the cd drive does not spin and no sound comes out.

However, if I try playing the CD in Amarok, it works perfectly fine. CD drive spins up and music comes out.

Has anyone else had this problem?

Thanks. -Noel

---

### Post by terminalspin on 2007-04-23
This is happening to me too now. I'm assuming that it is due to some update, because I used to be able to play CDs fine on this machine until recently. 

I'm running Edgy on an Intel 945 Core2Duo.

Both DVD drives exhibit the same problem, under Sound Juicer, Grip & Kaudiocreator.

No error messages, no logs, the system just hangs shortly after starting to read the first track. The whole machine crashes with no response from the mouse or keyboard.

DVD video works fine in both drives, as do data CDs.

Does anyone have any idea where to start looking?

---

### Post by nlvivar on 2007-04-23
That's funny because my dvd didn't work when I did a clean install of 6.10. However, I recently did a network upgrade to 7.04, and the dvd drive works decently well now.

Sound-juicer is still flakey (it hangs when I try to change the encode options), but I can easily rip+encode using Grip, which is what I'm used to anyways.

Weird stuff. I've never found what's wrong. What kind of computer and dvd drive do you have?

---

### Post by borkabrak on 2007-04-24
I'm having the same problem, and it's *infuriating*.  

Whenever I try to read a CD in sound juicer or banshee or kscd, the system takes about thirty seconds or so to completely freeze, responding to no mouse movements or key commands.  The only thing it responds to is being turned off.  The odd thing is that Amarok *will* read the CD.  I'm still trying to figure out why, but I can't really do that right now, for reasons I hope are obvious.  :)

I have previously been able to rip/play CDs on this machine, on exactly the same hardware.  I don't recall fiddling with anything too audio/cd specific in the software, but I do install whatever updates it suggests.

My machine is a Dell Latitude D820.  The OS is Ubuntu Edgy Eft 6.10.  The drive seems to have this information associated with it:  DVD+RW SDVD8820.

This problem began occurring something like a week ago, but may have been as far back as the beginning of April.

Someone who knows, *please* read this.  It's driving us crazy.  I *like* my music.  :)

---

### Post by terminalspin on 2007-04-24
I'm using a home built machine:-

Motherboard - Gigabyte GA-945P-S3 
Processor - Intel Core2Duo E6400
DVD-ROM - Liteon (DVD SHD-16P1S)
DVD-RW - Optiarc (DVD_RW AD-7170a)
On-board sound - Realtek ALC883

Like Borkabrak I have been using this machine & OS to successfully play CDs, so I reckon it must be an update that caused the problems.

I made a wild guess that it might be cdparanoia because that seemed to have been updated in the edgy-backports. (it is also a dependency of sound-juicer grip and ripperx etc).

I reverted to the earlier version, but that just made soundjuicer crash on startup.

I'm going to have a look for recently upgraded CD audio related libraries and meddle with them...

Any thoughts as to whether gstreamer might be responsible?

---

### Post by borkabrak on 2007-04-24
I was thinking it had something to do with gstreamer as well, terminalspin, but that's really a guess based on what I *think* are the dependencies.

Amarok does depend on xine, and unsurprisingly, gxine will play them, too.  Also vlc, though I don't know yet what it uses.

So the problem does definitely seem to be somewhere in the audio layer itself, or with a common interface to it.  Gstreamer seems a likely candidate, but the problem might still reside in a component of *it*, such as cdparanoia (does gstreamer use cdparanoia?)

Hrm.. I guess that's *some* progress..  

I guess I'll start grovelling through man pages, looking for common dependencies..  ugh.

---

### Post by terminalspin on 2007-04-24
Fixed it!!!

I am now listening to The Clash in glorious 2 channel technicolor.

Fortunately my neighbours are music lovers...

It looks like I was on the right track with the cdparanoia thing.

the bug is detailed here [https://bugs.launchpad.net/ubuntu/+source/cdparanoia/+bug/106000]("https://bugs.launchpad.net/ubuntu/+source/cdparanoia/+bug/106000")

For those whose apt foo is as bad as mine, steps to correct it in edgy appear to be:-
1. fire up synaptic.
2. select cdparanoia.
3. from the menu bar click "package" and select "force version"
4. in the pop-up dialogue, select the previous version "3a9.8-13 edgy"
5. do the same for package libcdparanoia0. (this is the bit I forgot to do, the first time)
6. click apply.

it then removes libcdparanoia-dev as well. (Who installed the dev package? I don't think it was me...)

Oh yeah, the auto-update tells me that there are updates available for cdparanoia, but I'm not biting this time, matey.

How do you tell apt that you don't want this update?

---

### Post by borkabrak on 2007-04-26
Rock *on*, terminalspin!  

Thanks a ton for that.  This fixed the problem for me, too.

Unfortunately, as you mentioned, now I have an update notification that I don't want to install.  There must be some way to turn that off.. 

I wonder how this got released..  Is it just a few machines that are affected?  But ours seem fairly different..  hrm..

Anyway, thanks a million again.

---

### Post by borkabrak on 2007-04-26
Well, it looks like you can do this:

-Go into your Repository configuration (either by going Settings->Repositories in Synaptic, or right-clicking the notification icon)

-Select the 'Internet Updates' tab.

-Uncheck the 'Backported Updates' option

Unfortunately, this only works because these to updates are both backports, and this method doesn't allow you to be automatically notified of other backports you may want.

*shrug*

---

### Post by borkabrak on 2007-05-11
And of course a better way to fix the version without turning off all backports is to highlight the package, then select from the menu, Package->Lock Version

Just FYI, I've got a coworker on identical hardware who's upgraded to Feisty and never experienced this problem.  Although his adventures during the upgrade were.. a bit stressful.  But that's for a different thread.

---

### Post by eleach on 2007-07-10
terminalspin -

Thanks! Was having the same problem and fortunately found this thread.

Ed

---

### Post by catfishk on 2007-08-12
my thinkpad T60 is hanging on audio cds, as well.  a downgrade of cdparanoia to v3a9.8-13(edgy) hasn't solved the issue

 data cds mount and open fine, however

---

### Post by catfishk on 2007-08-12
in addition, dvd playback is also working, audio and video

---

### Post by jmate24 on 2007-08-12
Audio CDs Hang...

it has happened to me too..
but I have only 256MB RAM,
64 of it is shared with my video

but then i wiped my computer and started fresh with 6.06.1 Ubuntu Alternate and updated and upgraded to 6.10 then again to 7.04 and it works. Just backup data before you do so.

P.S.
try seeing if your CDs and DVDs are scratched that may be causing your problem

P.S.S.
There is a package in synaptic that provides CD/DVD Error Correction. :)

---

