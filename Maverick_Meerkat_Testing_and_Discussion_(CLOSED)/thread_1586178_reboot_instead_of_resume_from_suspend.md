---
title: "reboot instead of resume from suspend"
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by joop! on 2010-10-01
After installing Meerkat 64bit on a Sony Vaio VPCF11S1E my laptop reboots and starts with grub2 instead of resuming my session.

The log of pm-suspend (/var/log/pm-suspend.log) shows no errors and ends with:
> Fri Oct  1 21:32:45 CEST 2010: performing suspend

Installing and suspending with uswsusp doesn't change anything.

Any ideas where to look to change this behaviour?

---

### Post by cariboo on 2010-10-01
If your are seeing the grub menu, it sounds like you are coming from hibernation instead of suspend. By default my system drops into hibernation after 30 minutes.

---

### Post by psusi on 2010-10-01
Yes, uswsusp hibernates.  After grub, it will resume from the hibernation.

---

### Post by danyzoca on 2010-10-01
The same happens with me. Hibernate works fine, although a little slow, but whenever I suspend, the process seems to work fine, but clicking when I click the power button again, the computer just boots up normally. Seems it "forgets" its suspended state. 

Also on a Sony Vaio Laptopo (VPCEB1S1E/BJ)

---

### Post by joop! on 2010-10-01
@ cariboo907:
No it's not hibernation. Hibernation works fine, just as danyzoca reports. It's only with the suspend/resume cycle where things go wrong

@psusi: I think uswsusp can both resume and hibernate. But that's not my point. This behaviour shows also up without using uswsusp

---

### Post by Quackers on 2010-10-01
Hmm strange. I have a vaio and in both Lucid and Meerkat suspend/resume works flawlessly. In both versions if I choose hibernate the system just shuts down but if I press the AV mode button or the start button the laptop boots normally through grub (but refuses to initialise my webcam - which isn't normally a problem on a cold boot).

---

### Post by cariboo on 2010-10-01
> **joop! said:**
> @ cariboo907:
No it's not hibernation. Hibernation works fine, just as danyzoca reports. It's only with the suspend/resume cycle where things go wrong

@psusi: I think uswsusp can both resume and hibernate. But that's not my point. This behaviour shows also up without using uswsusp

My system goes through grub when coming out of hibernate, and the desktop is in the same state as it was when it went into hibernate. To come out of suspend all I have to do is touch the any key.

Here's my suspend log.

```
Fri Oct  1 16:06:49 PDT 2010: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux redstone 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3261  0 
nls_cp437               4931  0 
vfat                    9201  0 
fat                    48240  1 vfat
usb_storage            40172  0 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
xt_limit                1394  7 
xt_tcpudp               1927  7 
ipt_addrtype            1611  4 
xt_state                1014  7 
ip6table_filter         1275  1 
ip6_tables             11764  1 ip6table_filter
nf_nat_irc              1168  0 
snd_hda_codec_idt      54887  1 
nf_conntrack_irc        3348  1 nf_nat_irc
nf_nat_ftp              1398  0 
snd_hda_intel          22107  2 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
nf_conntrack_ftp        5361  1 nf_nat_ftp
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1302  1 
ip_tables              10460  1 iptable_filter
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
joydev                  8735  0 
snd_rawmidi            17783  1 snd_seq_midi
lib80211_crypt_tkip     7736  0 
snd_seq_midi_event      6047  1 snd_seq_midi
i915                  290938  4 
wl                   1959533  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
drm                   168054  5 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                  5191  0 
uvcvideo               55847  0 
i2c_algo_bit            5168  1 i915
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
video                  18712  1 i915
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2633  0 
lp                      7342  0 
soundcore                880  1 snd
intel_agp              26360  2 i915
output                  1883  1 video
serio_raw               4022  0 
agpgart                32011  2 drm,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lib80211                5058  2 lib80211_crypt_tkip,wl
parport                31492  3 parport_pc,ppdev,lp
ahci                   19013  0 
libahci                21667  4 ahci
atl1c                  29949  0 
             total       used       free     shared    buffers     cached
Mem:       1017292     523856     493436          0      17764     303728
-/+ buffers/cache:     202364     814928
Swap:      1951740      56952    1894788

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.269 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0


```

---

### Post by Quackers on 2010-10-01
cariboo907 where would my suspend log be and what would it be called? Also is there a hibernate log as well? Thanks.

/var/log/pm_suspend I think it was. I found that one. No hibernate one though yet.

---

### Post by cariboo on 2010-10-01
The os uses /var/log/pm-suspend.log for both hibernate and suspend. An easy way to view log files is to use System->Administration->Log File Viewer.

---

### Post by Quackers on 2010-10-02
Thank you cariboo907.

---

### Post by joop! on 2010-10-02
> My system goes through grub when coming out of hibernate, and the desktop is in the same state as it was when it went into hibernate. To come out of suspend all I have to do is touch the any key.

Yes, cariboo907. I agree with your description about the differences between hibernation and suspend. And as said, hibernation goes well. It takes some more time, goes through grub and after a while my session is back as it was. When in hibernation, my laptop looks turned off. The log of pm-suspend tells me:
```
Fri Oct  1 22:59:29 CEST 2010: Running hooks for hibernate.
```
In the other case, when suspended, my laptop is having an nice orange light blinking and awakening can be done with any key. However, after suspending my system also goes through grub but does **not** restore my session. It's a fresh restart, and an application like firefox apologizes for crashing. The log of pm-suspend tells me in this case:
```
Fri Oct  1 21:32:38 CEST 2010: Running hooks for suspend.
```

So again the question I started this post with: Any ideas where to look to change this behaviour?

---

### Post by auxbuss on 2010-10-02
I can confirm this behaviour on a Sony Vaio VPCF11M1E. This is 32-bit.

All worked well on Lucid, but on upgrading, a month or so back, suspend no longer works, in the manner you describe.

I have done quite a bit of work trying to diagnose this, but have hot had any success. I'm delighted to find this thread today, as now I'm not alone :-)

Just to confirm, when suspending or hibernating, the machine does the things you'd expect it to do: hibernate does a lot of writing to disk, and suspend ends by flashing the power button (and turns orange on this machine). The logs also show no errors. They show a successful suspend or hibernate.

I'm convinced that it's the restart that's the issue, because there is no attempt to do anything but cold boot. It's immediate.

I also looked here, but found nothing useful: [http://code.google.com/p/vaio-f11-linux/](http://code.google.com/p/vaio-f11-linux/)

---

### Post by auxbuss on 2010-10-02
There is another user with this behaviour.

See #16 here: [http://code.google.com/p/vaio-f11-linux/issues/detail?id=23](http://code.google.com/p/vaio-f11-linux/issues/detail?id=23)

(My post is #17)

---

### Post by joop! on 2010-10-02
> **auxbuss said:**
> I can confirm this behaviour on a Sony Vaio VPCF11M1E. This is 32-bit.

So it's both in 32bit and 64bit. Interesting to notice.

> All worked well on Lucid, but on upgrading, a month or so back, suspend no longer works in the manner you describe.

For me it was a fresh install, but it's true that with previous versions everything is working fine.

> I have done quite a bit of work trying to diagnose this, but have hot had any success. I'm delighted to find this thread today, as now I'm not alone :-)
You are never alone, even when you think you are....

> I'm convinced that it's the restart that's the issue, because there is no attempt to do anything but cold boot. It's immediate.

I noticed in the changelogs of pm-utils quite a lot of changes. I am just guessing this problem might have it's origin here. Does anyone know how the mechanism of resume works? What is triggering the hardware to resume instead of restart?

> I also looked here, but found nothing useful: [http://code.google.com/p/vaio-f11-linux/](http://code.google.com/p/vaio-f11-linux/)
Issue 23, which you are mentioning in your next post, is different from this one, I think. That one is about not suspending right, and not about restarting after a succesful suspend.

---

### Post by Quackers on 2010-10-02
I'm using 64 bit Meerkat and as previously mentioned my suspend and resume work flawlessly, as they did with Lucid (in both 32 bit and 64 bit). I only have an odd resume from hibernate.

---

### Post by joop! on 2010-10-02
> **Quackers said:**
> I'm using 64 bit Meerkat and as previously mentioned my suspend and resume work flawlessly, as they did with Lucid (in both 32 bit and 64 bit). I only have an odd resume from hibernate.

It's quite common that suspend problems are hardware related. Your Sony vaio is having quite different hardware then the vaio F11 series

---

### Post by auxbuss on 2010-10-02
Do you want to help compile a bug report for launchpad?

I tried posting a bug against linux a week or so back, but launchpad crashed twice uploading, so I gave up.

---

### Post by psusi on 2010-10-02
The best thing you can do is try out different kernels to see which ones work and which ones don't.  You might want to read [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) and [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds).

If you can narrow down which kernels work and which don't, and file a bug report, that will make it much more likely someone will be able to figure out what is wrong.

---

### Post by joop! on 2010-10-02
I agree with psusi it makes sense to narrow down the problem before posting a bug report.
That's why I am really interested why psusi suggests it is related with the kernel and not pm-utils or any other sofware. Please shine a light on that!

---

### Post by psusi on 2010-10-02
Because it is the kernel that actually does the suspend, with help from the bios.  The user mode tools just ask it to and take care of things like locking the screen when you resume.

---

### Post by auxbuss on 2010-10-02
I was running 2.6.35-02063505 until about a week ago for a couple of weeks.

You can't go back to the Lucid kernels. They won't work.

---

### Post by joop! on 2010-10-02
> **psusi said:**
> Because it is the kernel that actually does the suspend, with help from the bios.  The user mode tools just ask it to and take care of things like locking the screen when you resume.

I guess you are right psusi. To verify I installed the mainline kernel I am still using on another partition, with ubuntu 9.10. With that kernel (2.6.32-0206322109) also my Meerkat system is resuming properly.

So now the task to figure out where this behaviour changed.

---

### Post by joop! on 2010-10-02
> **auxbuss said:**
> I was running 2.6.35-02063505 until about a week ago for a couple of weeks.

You can't go back to the Lucid kernels. They won't work.

And was that kernel resuming properly? Or did it have the same problem?

---

### Post by auxbuss on 2010-10-02
Sorry. No it didn't resume properly. Same problem.

(I was using it to test a USB issue for the devs. Although I hoped it would fix this issue, of course.)

---

### Post by auxbuss on 2010-10-02
Let me know if you want help. Just let me know which kernel you want tested.

---

### Post by joop! on 2010-10-02
For sure I need help. Although I don't know how.


Let me explain. I installed the mainline kernel 2.6.35rc1. Which resumed perfectly well. After that I restarted the current Maverick kernel, about which I started this thread (2.6.35-22 from the ubuntu repos). And of course, now also this kernel resumed perfectly well! :confused:

So now I don't get it anymore. I have no clue what changed this behaviour. Maybe some post-installation script? And what will happen when I remove the extra installed kernels?

---

### Post by auxbuss on 2010-10-02
2.6.35rc1 is labelled Lucid (v2.6.35-rc1-lucid). Is that the one you tried?

---

### Post by joop! on 2010-10-02
> **auxbuss said:**
> 2.6.35rc1 is labelled Lucid (v2.6.35-rc1-lucid). Is that the one you tried?

Yes. To be precise: I first installed [this]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.21.9-lucid/") (see my post #22) and after that [this]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/") (my post 26)
I didn't try the Maverick kernel in between these installs, so I don't know which of the two installs had an effect (if any).

Interesting if you can reproduce the same.

And to answer my own last question: resume is still working fine after removing these extra kernels (so far...)

---

### Post by auxbuss on 2010-10-02
Okay. I tried v2.6.35-rc1-lucid.

In this case, resume from suspend was attempted, but the monitor did not switch on. I didn't try ssh'ing in, but it seemed like it was a normal resume otherwise.

I will try the 9.10 kernel you tried and see where I get to with that.

I also noticed, because I have remove quiet splash from the kernel call, that recent kernels are not failing to set some sensors. This is at the end of the bot process, so unrelated. But there are definitely other issues.

I really think we should bring this to the attention of the devs, as it might be a bigger problem come the official release of 10.10.

---

### Post by joop! on 2010-10-02
> **auxbuss said:**
> Okay. I tried v2.6.35-rc1-lucid.

In this case, resume from suspend was attempted, but the monitor did not switch on. I didn't try ssh'ing in, but it seemed like it was a normal resume otherwise.

Notice that after resume the screen is blanked, like when the screensaver is activated. At least in my case. I first have to use my touchpad to get to the unlock box.

---

### Post by auxbuss on 2010-10-02
I installed 2.6.32-0206322109 while using 2.6.35-020635rc1.

For the heck of it, I suspended, expecting the resume to fail, as it had before with this kernel. But instead, resume worked!

So, I am still using 2.6.35-020635rc1, but simply installing 2.6.32-0206322109 has made resume from suspend work.

This seems very similar to your case. How very strange,

---

### Post by auxbuss on 2010-10-02
I tried to suspend/resume a second time, after the above, while still using 2.6.35-020635rc1, and it resumed with a blank screen. Keyboard was dead and touchpad didn't have any affect.

I tried booting into the latest Maverick kernel and that reverted to the original behaviour: cold boot on resume from supsend.

Will now try booting into the Lucid kernel linux-headers-2.6.32-0206322109.

---

### Post by auxbuss on 2010-10-02
Using 2.6.32-0206322109 I can suspend and resume multiple times without problems.

So, something has changed. What next?

---

### Post by joop! on 2010-10-02
I have no clue what to do next. Too bad things are not getting clear at all.

I leave it for while and will observe my system. When I figure something out, I will post again.

---

### Post by behnaam on 2010-10-03
I have the exact same issue on my Sony Vaio VPCF11SE running 32bit Maverick.

This happened when I upgraded to mainline kernel 2.6.36-r3 and also on 2.6.36-r6.

Really strange issue, any progress on finding the source to this behavior?

---

### Post by cariboo on 2010-10-03
@behnaam, does that mean suspend was working properly for you with the default kernel?

---

### Post by auxbuss on 2010-10-03
I have some feedback.

As joop! did, I installed 2.6.32-0206322109.

After using this for a while, I reverted to using the current Maverick kernel (2.6.35-22-generic). This kernel now resumes from suspend. It has never done so before.

This fixes, at least temporarily, my suspend issues, as it did for joop!

(Aside: I have been using 2.6.32-0206322109 all day. It is w-a-y faster in Gnome than the current mainline Maverick kernel. It also does not have a lot of the regressions, that I experience, that the mainline kernel currently exhibits. I will be using 2.6.32-0206322109, rather than the mainline until the mainline is fixed.

That said the resume issue might have been masking other issues that are also now "fixed". For example, a quick look at my process count shows that it has dropped from its usual 125 to 130, to 115. So, I will try the mainline kernel for a day and see how it goes.)

---

### Post by behnaam on 2010-10-06
> **cariboo907 said:**
> @behnaam, does that mean suspend was working properly for you with the default kernel?

Yes it did :/

---

### Post by auxbuss on 2010-10-06
Just noticed a grub change go through that appears to have fixed resume here. It's hard for me to confirm this as a fix as the latest 260.19 Nvidia drives don't work on the 10.10 latest kernel so I'm having to use 256.53 from Nvidia and these won't build against 2.6.32-0206322109 due to gcc version conflicts. What a mess!

/etc/grub.d/00_header added:
```

	# video_bochs and video_cirrus require probing PCI space, and some
	# machines don't seem to like this.  These are generally
	# non-essential at least for i386-pc, so disable them as a
	# short-term fix for Ubuntu 10.10.
	case "${backend}" in
	    video_bochs|video_cirrus)
		cpu="$(uname -m)"
		case "${cpu}" in
		    i[3456]86|x86_64)
			[ -d /sys/firmware/efi ] || continue
		    ;;
		esac
	    ;;
	esac

```

---

### Post by behnaam on 2010-10-07
> **auxbuss said:**
> Just noticed a grub change go through that appears to have fixed resume here. It's hard for me to confirm this as a fix as the latest 260.19 Nvidia drives don't work on the 10.10 latest kernel so I'm having to use 256.53 from Nvidia and these won't build against 2.6.32-0206322109 due to gcc version conflicts. What a mess!

/etc/grub.d/00_header added:
```

	# video_bochs and video_cirrus require probing PCI space, and some
	# machines don't seem to like this.  These are generally
	# non-essential at least for i386-pc, so disable them as a
	# short-term fix for Ubuntu 10.10.
	case "${backend}" in
	    video_bochs|video_cirrus)
		cpu="$(uname -m)"
		case "${cpu}" in
		    i[3456]86|x86_64)
			[ -d /sys/firmware/efi ] || continue
		    ;;
		esac
	    ;;
	esac

```

Good progress.

I managed to build 256.53 against 2.6.32-0206322109

This is what I did:

1. Add Intrepids universe repos to sources.list
2. Now install GCC-4.2 > sudo apt-get install gcc-4.2
sudo apt-get install g++-4.2
3. Remove previous GCC symlinks and symlink to gcc-4.2 to instead, like this (OBS! only for 32-bit systems):
> cd /usr/bin
sudo rm cpp gcc g++
sudo ln -s g++-4.2 g++ 
sudo ln -s gcc-4.2 gcc
sudo ln -s cpp-4.2 cpp
4. Finished, time to sudo sh nvidia-installer*.run!

Worked perfectly fine!

---

### Post by auxbuss on 2010-10-07
Nicely done, but that's too much hackery for me. I guess it's time to change distros. Too many regressions in Ubuntu these days for me, and it's taking far too much time to resolve issues. I guess I'm no longer the target for Ubuntu. Thanks.

---

### Post by pulmro on 2010-10-07
I have a Sony Vaio VPCEB1Z1E and passing the option **acpi_sleep=nonvs** to the kernel **solved** the issue of rebooting instead of resuming from suspend. As you can read here problems started when was introduced (in 2.6.35-rc4) saving NVS area during suspend:
[http://www.spinics.net/lists/linux-acpi/msg29521.html](http://www.spinics.net/lists/linux-acpi/msg29521.html)

So you need to modify /boot/grub/grub.cfg to pass that option to the kernel, like this:
```
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set 5ae3fe0b-ef15-4af0-a452-71b09868467f
        linux   /boot/vmlinuz-2.6.35-22-generic root=UUID=5ae3fe0b-ef15-4af0-a452-71b09868467f ro   quiet splash **acpi_sleep=nonvs**
        initrd  /boot/initrd.img-2.6.35-22-generic
}
```

---

### Post by behnaam on 2010-10-07
> **auxbuss said:**
> Nicely done, but that's too much hackery for me. I guess it's time to change distros. Too many regressions in Ubuntu these days for me, and it's taking far too much time to resolve issues. I guess I'm no longer the target for Ubuntu. Thanks.

Yeah, while trying to fix the suspend issue I managed to screw my Ubuntu installation. Had to add vmalloc option to grub config to get it to boot and now that I tried with NVIDIA 260.19.04 everything broke again. I hate this so much and the logs tell me absolutely nothing. Spent the last 12h trying to solve everything.

> **pulmro said:**
> I have a Sony Vaio VPCEB1Z1E and passing the option **acpi_sleep=nonvs** to the kernel **solved** the issue of rebooting instead of resuming from suspend. As you can read here problems started when was introduced (in 2.6.35-rc4) saving NVS area during suspend:
[http://www.spinics.net/lists/linux-acpi/msg29521.html](http://www.spinics.net/lists/linux-acpi/msg29521.html)

So you need to modify /boot/grub/grub.cfg to pass that option to the kernel, like this:
```
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos5)'
        search --no-floppy --fs-uuid --set 5ae3fe0b-ef15-4af0-a452-71b09868467f
        linux   /boot/vmlinuz-2.6.35-22-generic root=UUID=5ae3fe0b-ef15-4af0-a452-71b09868467f ro   quiet splash **acpi_sleep=nonvs**
        initrd  /boot/initrd.img-2.6.35-22-generic
}
```

Thanks for the find! Will try it ASAP :)

---

### Post by auxbuss on 2010-10-07
acpi_sleep=nonvs is working for me, so far. Thanks.

Interesting bug thread. I don't know anything about NVS, so many blanks in it, but I got the gist of it.

---

### Post by jacetegan on 2010-10-07
First, be sure your anti-virus software has the latest definitions and run a
virus scan. If your system is clear of viruses, open Control Panel, open System, go to
the Advanced tab, click Settings under Start-up and Recovery, remove the
check from "Automatically Restart" under System Failure.

---

### Post by auxbuss on 2010-10-07
Meant to say that the right place to add this, I believe, is /etc/default/grub rather than /boot/grub/grub.cfg, because the latter will be silently overwritten periodically.

---

### Post by psusi on 2010-10-07
Weird... NVS means non volatile storage, as in doesn't get lost during hibernate or suspend.  The ACPI standard REQUIRES the kernel to save and restore it during suspend/hibernate.

---

### Post by tgui on 2010-10-07
The NVS hack works for me as well. I hope future kernel upgrades don't need this. I don't want to alter grub every time I pull a new kernel.

---

### Post by psusi on 2010-10-07
> **tgui said:**
> The NVS hack works for me as well. I hope future kernel upgrades don't need this. I don't want to alter grub every time I pull a new kernel.

You won't have to if you added it to /etc/default/grub.

---

### Post by pulmro on 2010-10-07
Quoting this [kernel patch]("http://www.spinics.net/lists/linux-acpi/msg30255.html"):> To keep track of the systems that require
 this workaround and to make the life of their users slightly easier
 blacklist them in acpisleep_dmi_table[].

So if we could get DMI_SYS_VENDOR & DMI_PRODUCT_NAME of our laptops and send them to kernel developers we could help building that list for next kernel versions.

---

### Post by kimyoungil on 2010-10-07
This might be a bit off-topic, but some other people looking for a solution to their problems might find it useful. I had the same symptoms, but for me this worked: [https://help.ubuntu.com/community/PowerManagement/Hiberate](https://help.ubuntu.com/community/PowerManagement/Hiberate)
(notice the spelling error in the link-name :p)
I put the correct swap partition in grub (resume=/dev/sdax)

---

