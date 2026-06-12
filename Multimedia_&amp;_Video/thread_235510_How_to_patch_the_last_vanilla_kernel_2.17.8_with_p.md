---
title: "How to patch the last vanilla kernel 2.17.8 with patch-2.6.17-rt8 ?"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by floogy on 2006-08-13
Hello,

I followed the steps to install realtime-lsm and I did this:

[http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#Real-Time_Support](http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#Real-Time_Support)

I got several xruns, and beep-media-player stoped playing after the first xrun. Therefore I tried to build a patched vanilla kernel using these Documents:
[http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption](http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption)
[http://people.redhat.com/mingo/realtime-preempt/patch-2.6.17-rt8](http://people.redhat.com/mingo/realtime-preempt/patch-2.6.17-rt8)

Unfortunately I got problems patching the kernel, and due to this I patched the 2 rejected chunks in Makefile and kerne/sched.c by 'hand'.

Maybe my earlier xrun problems appeared due to conflicts between realtime-lsm module with the rlimits-aware PAM ??

Anyway, I compiled the kernel after a 'make oldconfig' and unfortunately enabled some other new options for debugging latency etc.

The step make modules stopped with two errors regarding realtime-lsm and avm-fritz. I ignored that, because I didn't want to use these modules, because realtime-lsm seems to be depricated in dapper, and I don't use fritz-avm/isdn anymore.

See also this thread in LKML:
[http://lkml.org/lkml/2006/8/12/195](http://lkml.org/lkml/2006/8/12/195)
[http://lkml.org/lkml/2006/8/13/31](http://lkml.org/lkml/2006/8/13/31)

Then I installed the new kernel, but it doesn't work at all, and fsck.ext3 crashes with SIGSEGV 11. After pressing CONTROL-D to start normal my computer reboots without any further messages.

Should I not use 'make oldconfig' because that can lead into wrong kernel configuration, or appears this bad behaviour due to a bad rt patch?

One reason might be, that the newr kernels are using a modified udev, that isn't in dapper?

Another idea is, that it's due to the fixed [nfs/ext3 ]("http://lkml.org/lkml/2006/7/17/41")bug ???

Any insights or ideas? 

Gerhard

---

### Post by hanzomon4 on 2006-08-13
Try to patch the 2.6.17 kernel version with the rt8

---

### Post by dolson on 2006-08-13
And do not use realtime-lsm on dapper.

---

### Post by floogy on 2006-08-14
I managed it to compile the kernel 2.17.8-rt8 (applied the patches, as described in LKML, by 'hand', maybe the patch in my LKML thread works for you).

The second time I did not use 'menu oldconfig' and followed exactly the instructions on ubuntustudio.

It works now, but the latency seems to be the same as with the stock kernel. Hmmm... I expected an Improvement over the dapper stockkernel and the appropriate commmands to enable rt on dapper with the stock kernel.

Therefore I think the first try failed because I enabled one other harmful kernel option by using 'make oldconfig', and said 'y' or 'm' on the wrong places ;-)

---

### Post by dolson on 2006-08-14
The latency is not going to be improved just by the -rt patch. You have to be running your applications in realtime, and you have to have JACK configured to whatever latency you want. The -rt patch is going to give you a nearly 100% pre-emptible kernel, which means you can lower your latency and not experience buffer underruns or overruns. It does not change your latency.

---

### Post by floogy on 2006-08-15
> **dolson said:**
> The latency is not going to be improved just by the -rt patch. You have to be running your applications in realtime, and you have to have JACK configured to whatever latency you want. The -rt patch is going to give you a nearly 100% pre-emptible kernel, which means you can lower your latency and not experience buffer underruns or overruns. It does not change your latency.

I'm using already jack with qjackctl. I tested exactly the same settings as in the tutorial of ubuntustudio, and now I use this settings (Realtime is checked in the checkbox):
```
/usr/bin/jackd -R -t5000 -dalsa -dhw:0 -r48000 -p64 -n2 -D -Cplug:dmix -S -i2 -o2
```

But I got after 5 seconds or so a lot of ["delay exceeding spare time"]("http://www.ubuntuforums.org/showpost.php?p=1379568&postcount=2") errors. 

I think due to these errors I got a lot of xruns.

Xruns are buffer underruns, are they? I'm sorry, but I'm completely new to this Realtime audio stuff.

Gerhard

[1] [delay exceeding spare time]("http://www.ubuntuforums.org/showthread.php?t=234884")
[2] [performance with amd64]("http://www.ubuntuforums.org/showpost.php?p=1379568)


--

---

### Post by floogy on 2006-08-17
Hmmm... I figured out how to get a single irq for my onboard sound, but the xrun/delay problem persists. I turned on CONFIG_HZ=1000, and recompiled the rt kernel. I set also the latency with setserial, and the application priority with rtch. All that didn't help.

Therefore I think it's due to the onboard sound of the nvidia ck804, because midi/hydrogen seems to work fine (or is hydrogen not midi?). 

I habe an asus A8N-SLI Deluxe motherboard with nvidia nforce onboard sound.

Also some player like alsaplayer work fine. Is that maybe due to crappy implementation of jack in the other apps (xine-libasyn-jack-plugin , jacklauncher)? Or do I need a good soundcard in the first place?

I don't have any clue.

If I really need a sound card, which card would you suggest for medium till lower, semi pro SoHo Hifi requirements?

EDIT:
I found this:
[http://ccrma-mail.stanford.edu/pipermail/planetccrma/2005-November/010718.html](http://ccrma-mail.stanford.edu/pipermail/planetccrma/2005-November/010718.html)
[http://article.gmane.org/gmane.linux.audio.users/26129/match=http+ubuntustudio+com+wiki+index+php+breezy+rlimits+aware+pam](http://article.gmane.org/gmane.linux.audio.users/26129/match=http+ubuntustudio+com+wiki+index+php+breezy+rlimits+aware+pam)
[http://www.music.columbia.edu/pipermail/linux-audio-user/2006-August.txt](http://www.music.columbia.edu/pipermail/linux-audio-user/2006-August.txt)
and this breezy PAM patch HOWTO:
[http://ubuntustudio.com/wiki/index.php/Breezy:Rlimits-Aware_PAM](http://ubuntustudio.com/wiki/index.php/Breezy:Rlimits-Aware_PAM)

I didn't patch PAM on my amd64 dapper to be rtlimits aware, though. Does that apply to dapper too?

Ok, I think all my problems with delays and xruns are maybe due to a rlimits-unaware PAM in dapper:
[http://ubuntustudio.com/wiki/index.php/Talk:Using_set_rlimits](http://ubuntustudio.com/wiki/index.php/Talk:Using_set_rlimits)
But this is disappointing:
[http://ubuntustudio.com/wiki/index.php?title=Rlimits-Aware_PAM_with_Dapper](http://ubuntustudio.com/wiki/index.php?title=Rlimits-Aware_PAM_with_Dapper)

Do I have to patch glibc, bash and PAM on dapper amd64 or can I find such Packages on ubuntustudio.com?

Thanks in advance.

Regards

Gerhard

---

### Post by dolson on 2006-08-17
Do not use the Breezy tutorials from UbuntuStudio.com on a Dapper install. Use the Dapper tutorials. Dapper ships with a patched PAM already.

Xruns are either buffer underruns or buffer overruns. The X means either over or under. Please read this: [http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#Kernel_Preemption_.26_Xruns](http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#Kernel_Preemption_.26_Xruns)

---

### Post by floogy on 2006-08-17
But [this]("http://ubuntustudio.com/wiki/index.php/Talk:Using_set_rlimits")  seems to be related to dapper:
> Yes, you do have to launch it with set_rlimits. How else is qjackctl going to know to use realtime priorities? If we didn't need to use something to give realtime access such as set_rlimits, then it wouldn't be on this site. Note that this is the case up until such a time as Ubuntu includes a patched and configured PAM, which will eliminate the need for set_rlimits. Alternately, you can use the realtime-lsm module. --Dana 10:58, 2 February 2006 (EST)
[edit]
Rlimits-Aware PAM

Moved to this page for Dapper: Rlimits-Aware_PAM_with_Dapper Moved to this page for Breezy: Rlimits-Aware_PAM --Dana 06:57, 5 February 2006 (EST)

--snip-- For complete system support of RLIMIT_RTPRIO, two more things would be required:

    * glibc should be repackaged with RLIMIT_NICE and RLIMIT_RTPRIO added to bits/resource.h (this patch got applied to glibc CVS/-2.4 and should backport to 2.3.6 easily)
    * bash also should be patched to make the builtin ulimit show and modify RLIMIT_RTPRIO (ulimit -r). There's a patch in Fedora CVS, but I didn't manage to recompile/repackage bash on Dapper. Well ... 

Dana, some questions:

    * would you want to move this notes out from this discussion page to some "real" page?
    * I do have more complete instructions on repackaging pam with pbuilder on Dapper. These may not be fully correct, since I'm very new to Debian packaging, but it works for me. Should I put them somewhere, and if so, where?
    * should I upload my i386 .dep packages for Dapper? 

Too bad that #17348 just sits there unresolved ...

Breezy has PAM-0.76, I don't know if the above patches are enough to backport. Maybe someone can give it a try.

--Woho 14:16, 4 February 2006 (EST)

Your work is awesome. The wiki is to focus on the current stable version of Ubuntu ATM. Dapper stuff will come forward in the week of the release, and Breezy stuff will be moved to their own page for archival purposes. With just the info you provided and a quick google search, I was able to make a proper patch for Breezy's PAM and it's all good now. We can host a Dapper deb if Canonical doesn't put a patched PAM into Dapper (someone is requesting it, so hopefully they will do it). If you take the page that I did and modify the process (and patch!) to fit Dapper, do so and link it on the Dapper Notes page, that would be great. I don't run Dapper because it's under development and I prefer not having an unstable desktop. To be honest, I did try installing it yesterday, but it failed at bootup with something about /dev/sda, but that was running in a VM.. So I don't know. I'll have to find another hard drive and install it.

Thanks, I'm happy that you find it helpful.

I agree with you on Dapper, it's just that I'm a bleeding edge junkie ... I created a new page Rlimits-Aware_PAM_with_Dapper with build instructions. Probably that's enough for Dapper users, who should be able to build that way themselves.

--Woho 04:09, 5 February 2006 (EST)

I removed the info from above and replaced it with links to our pages, which are more complete. also renaming the page to make it match. --Dana 06:57, 5 February 2006 (EST) 

And how can I figure out, that dapper got a patched bash, glibc and PAM? Where can I find that?

And I knew that already, that xruns are buffer under- or overruns, but It seems to me, that I tried everything, and that was the last thing I didn't tried. Beside exchanging my crappy sound card, though.

BTW: all the dapper links are dead in that page.

EDIT: Ok I found that PAM bug closed:
[https://launchpad.net/distros/ubuntu/+source/pam/+bug/17348](https://launchpad.net/distros/ubuntu/+source/pam/+bug/17348)

Does this apply to bash and glibc too?

I thought everything with realtime and latency in audio has got to do with avoiding xruns, delays and to big latencies?

So, what would you suggest, to solve these problems?
And I'm wondering how one can achieve to know that the box is realtime enabled, and that the system is fine in rt capabilities?

---

### Post by dolson on 2006-08-17
The page you linked to is old. It is in the "Breezy Talk" namespace of the wiki, which is old. The dates are all from prior to Dapper's release, and so is the info. The discussion going on was regarding the development version of Dapper, and none of the links work anymore because that page is so old, and was created originally before we implemented separate namespaces in the wiki to separate the different distros.

You do not need set_rlimits if you have Dapper because Dapper has a version of PAM that does what set_rlimits does, but better. Set_rlimits is for distros without PAM at all, like Slackware, and is one means to achieve an end. The others are PAM, realtime_lsm, and running as root. PAM is the ideal, and what everyone on Dapper should be using.

As a side note, I am considering removing all 'outdated' (read: older than Dapper) content because this is the second time in a week that someone has been reading old and outdated info from Breezy while they are using Dapper. I run the risk of alienating Breezy users, but what choice do I have here? Some people are even installing the PAM packages I made for Breezy into Dapper, and screwing up their system...

As far as finding out if bash, glibc, or PAM are patched or not, it's simple. If you are in Dapper, it is patched. If you are in any Ubuntu release previous to Dapper, it is not patched. Look in the changelogs to have this confirmed if you want. You can search for my name in the PAM changelog, and I don't know who submitted the other patches, probably Lee Revell is what I am thinking.

I posted the info about Xruns because you just finished asking in one of your last posts what they were.

Most likely, your issues are caused by your sound card. I would invest in a new one. If you can't afford a pro card, like how I can't, then I recommend a cheap SB Live! 5.1 card. It isn't pro, but it works for me.

---

### Post by floogy on 2006-08-17
Hy, thank you for your suggestion on the SB Live! 5.1, I read somewhere a cheapo tutorial on combining two es1371 really cheap cards, and turn them by fusing them together by cables with puter (don't know the words*) into a don't know what semi prof card. Maybe I'm looking into that, but I think I'll stay with your suggestion ;-) , or will figure out if there is another good semi prof solution for SoHo.

Regarding the wiki you might place a huge, or really visible Warning at the top. I think that would be the best solution for the wiki.

Examples:
[http://gentoo-wiki.com/HOWTO_nForce2_hw_mixing#This_guide_is_all_wrong](http://gentoo-wiki.com/HOWTO_nForce2_hw_mixing#This_guide_is_all_wrong)
[http://wiki.ubuntuusers.de/Codecs](http://wiki.ubuntuusers.de/Codecs) Please search for the sentence "Achtung! (Attention!), to see the beautyfull red css box, which warns about something!

Thanks again.

regards

Gerhard


* I'm sorry for my bizarre somewhat english... ;-) I'll might improve it in the future...

---

### Post by dolson on 2006-08-17
IF you really need more than one stereo input simultaneously, you will want to save up. A lot of people ask on the LAU mailing list about using two sound cards, and yes, I've seen the hack job out there on the net, but it is very unrecommended, requires soldering your cards together, and is still not ideal.

There is a page on the wiki for hardware recommendations, and I had hoped more people would add their gear there to say what is good and what is not.

I think the M-Audio cards are fairly inexpensive, for the features, but I could be wrong.

I still want to get a better setup sometime, but until then, I just record a single stereo track at a time (or two mono tracks) with my SB Live! 5.1 or Audigy2 ZS. I do have a mixer that all of my hardware gear plugs into, the output of which goes to the line in of my card. Works ok if you're a solo musician or recording a live mix (stereo only, obviously).

---

