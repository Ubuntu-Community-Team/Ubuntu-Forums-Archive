---
title: "Ricotz ppa"
date: 2010-05-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by plun on 2010-05-07
For the ultimate kernel and audio freak....

[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

2.6.34-1 preempt kernel (based on RC5)

Alsa 1.0.23

:guitar:

---

### Post by autocrosser on 2010-05-07
Sounds good---

Hi plun!!!!!  good to see you again!!!!

---

### Post by plun on 2010-05-07
Heya autocrosser....):P

Forgot Daniel Chens newest PulseAudio package in the first message...1:0.9.22~0.9.21

;)

---

### Post by DougieFresh4U on 2010-05-07
> **autocrosser said:**
> Sounds good---

Hi plun!!!!!  good to see you again!!!!

> **plun said:**
> For the ultimate kernel and audio freak....

[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

2.6.34-1 preempt kernel (based on RC5)

Alsa 1.0.23

:guitar:
Hey plun and autocrosser ):P 
I would like to try your 'suggested' ppa but I am not sure how to add the key via terminal as I am sure your aware of the 'Softwarw Sources' issue that gets us at the start of every cycle - no access :mad:
I am currently using 2.6.34rc6 kernel

---

### Post by autocrosser on 2010-05-07
If you goto the PPA page & tic the "technical details" and then "what's this?" link there is all the info to manual add including the key...I just did it...

---

### Post by tekstr1der on 2010-05-07
> **DougieFresh4U said:**
> 
I would like to try your 'suggested' ppa but I am not sure how to add the key via terminal...

Hi. Is this not working for you?

```
:~$ sudo add-apt-repository ppa:ricotz/unstable

```

---

### Post by Slug71 on 2010-05-07
Thanks plun, will give it a whirl.

---

### Post by DougieFresh4U on 2010-05-08
> **tekstr1der said:**
> Hi. Is this not working for you?

```
:~$ sudo add-apt-repository ppa:ricotz/unstable

```

Yeah, still not getting the key, but it's functioning correctly, I just ignored the warning.
Thanks

---

### Post by plun on 2010-05-08
> **DougieFresh4U said:**
> Yeah, still not getting the key, but it's functioning correctly, I just ignored the warning.
Thanks

Heya Dougie

Solution:
[http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/](http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/)

---

### Post by DougieFresh4U on 2010-05-08
> **plun said:**
> Heya Dougie

Solution:
[http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/](http://ubuntu-tutorials.com/2009/05/14/add-ppa-key-to-your-apt-keyring/)

Thanks.
Actually, I managed to get at my 'Software Sources', as you know the 'problem' we always get at every cycle, which I sorted with the help of one of your post in another thread.

---

### Post by crjackson on 2010-05-09
> **plun said:**
> For the ultimate kernel and audio freak....

[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

2.6.34-1 preempt kernel (based on RC5)

Alsa 1.0.23

:guitar:

Having never jumped ahead in kernels (other than normal updates), what could I expect to get broken right away?  nVidia blob?  other?  Or will it pretty much be seamless?

also, if a kernel doesn't work for me, will ppa-purge work for kernels too?

---

### Post by plun on 2010-05-09
> **crjackson said:**
> 
also, if a kernel doesn't work for me, will ppa-purge work for kernels too?

Yep probably..... I have never removed a kernel with ppa-purge.

Always using Synaptic and searches for linux-image and linux-headers, thats it...:KS

(The kernel is also from Leann Ogasawara, Ubuntu developer..)

---

### Post by crjackson on 2010-05-09
> **plun said:**
> Yep probably..... I have never removed a kernel with ppa-purge.

Always using Synaptic and searches for linux-image and linux-headers, thats it...:KS

(The kernel is also from Leann Ogasawara, Ubuntu developer..)

What about breakage?  What's the norm to be expected?

---

### Post by plun on 2010-05-09
> **crjackson said:**
> What about breakage?  What's the norm to be expected?

I thrust Leann !  I also runs my Maverick on a test partition, let it break.

Back in 10 minutes or if I chroot and repair...

---

### Post by crjackson on 2010-05-09
> **plun said:**
> I thrust Leann !  I also runs my Maverick on a test partition, let it break.

Back in 10 minutes or if I chroot and repair...

Well, I want to test it in Lucid right now, I was concerned about nVidia driver breakage.

---

### Post by plun on 2010-05-09
> **crjackson said:**
> Well, I want to test it in Lucid right now, I was concerned about nVidia driver breakage.

Please note that this is Maverick testing and discussion, not Lucid !

---

### Post by crjackson on 2010-05-09
Yeah I know plun, I'm working with both and since the information is posted in this section just though I'd ask.  I"ll limit my question to Maverick going forward.

---

### Post by plun on 2010-05-12
New kernel based on RC7

Testing the preempt flavor myself, great performance:)

```
Changelog

linux (2.6.34-2.6~10.04~ricotz1) lucid; urgency=low

  [ Chase Douglas ]

  * enforce CONFIG_TMPFS_POSIX_ACL=y
    - LP: #575940
  * don't force module dependency checking
    - LP: #577029

  [ Kees Cook ]

  * SAUCE: mmap_min_addr check CAP_SYS_RAWIO only for write
    - LP: #568844

  [ Leann Ogasawara ]

  * Revert "SAUCE: ata: blacklist FUJITSU MHW2160BH PL"
  * rebase to v2.6.34-rc7
  * [Config] update configs following rebase to v2.6.34-rc7
  * [Config] update port configs following rebase to v2.6.34-rc7
  * Add btrfs to the udebs

  [ Tim Gardner ]

  * [Config] Add atl1c to nic-modules udeb
    - LP: #557130

  [ Upstream changes ]

  * rebased to v2.6.34-rc7

  [ Rico Tzschichholz ]
  * Build on lucid
  * Bump ABI

```

---

### Post by zika on 2010-05-12
When can we expect maverick branch...?

---

### Post by dino99 on 2010-05-12
6 hours to be built :P
not yet into repo

my system goes fatty: > 225000 files and folders installed , wow

---

### Post by plun on 2010-05-12
Ricotz kernel is ready, I am running it...(on Maverick)

Just search for linux-image and linux-headers with Synaptic.

Maybe a preempt kernel is a good choice...:guitar:

---

### Post by zika on 2010-05-12
> **plun said:**
> Ricotz kernel is ready, I am running it...(on Maverick)

Just search for linux-image and linux-headers with Synaptic.

Maybe a preempt kernel is a good choice...:guitar:```
zika@zika:~$ uname -a
Linux zika 2.6.34-2-preempt #04~ricotz1-Ubuntu SMP PREEMPT Wed May 12 13:38:26 UTC 2010 x86_64 GNU/Linux
``````
zika@zika:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu maverick (development branch)"
```I was, just, curious about getting on Maverick track... :)
The only generic kernel I have is 2.6.34-999...

---

### Post by maclancer on 2010-05-12
Can I install that kernel on 10.04 without screwing Ubuntu?

---

### Post by plun on 2010-05-12
> **maclancer said:**
> Can I install that kernel on 10.04 without screwing Ubuntu?

Please note that Ricotz ppa is marked "unstable"...

Maverick is also unstable so a user must be prepared that something can go wrong.


-----

@Zika

Ok...:)

I cannot see any trouble (at the moment) running Lucid ppas with Maverick.

Leann(Oga)  has also uploaded a kernel to Mavericks archive, building status ?

---

### Post by maclancer on 2010-05-12
Yup... not working properly in a GA P35 DS3L, I am going back to 2.6.32

---

### Post by Starks on 2010-05-12
> **plun said:**
> Please note that this is Maverick testing and discussion, not Lucid !
As far as I'm concerned, our machines are still more Lucid than Maverick right now with respect to repo content. A chimeric install if you will.

---

### Post by Starks on 2010-05-12
[LEFT]Can someone explain what a preempt kernel is?

I've been hearing it a lot over the past few weeks.
[/LEFT]

---

### Post by ratcheer on 2010-05-12
I cannot access the ricotz ppa for Maverick. It added to my repository and, when I ran aptitude update, it even retrieved the gpg key, but it gives a 404 not found on the repository, itself. Am I misunderstanding something?

Thanks,
Tim

---

### Post by zika on 2010-05-12
> **ratcheer said:**
> I cannot access the ricotz ppa for Maverick. It added to my repository and, when I ran aptitude update, it even retrieved the gpg key, but it gives a 404 not found on the repository, itself. Am I misunderstanding something?

Thanks,
TimNo Maverick branch on ricotz ppa, yet. Open Software sources, highlight ricotz ppa, edit maverick into lucid and remember to revert once Maverick branch is available...

---

### Post by ranch hand on 2010-05-12
> **ratcheer said:**
> I cannot access the ricotz ppa for Maverick. It added to my repository and, when I ran aptitude update, it even retrieved the gpg key, but it gives a 404 not found on the repository, itself. Am I misunderstanding something?

Thanks,
Tim
Are you sure they have a 10.10 repo?  Maybe you need to use the one for 10.04.

---

### Post by plun on 2010-05-12
> **Starks said:**
> [LEFT]Can someone explain what a preempt kernel is?

I've been hearing it a lot over the past few weeks.
[/LEFT]

Here is an howto from kernel.org

[https://rt.wiki.kernel.org/index.php/RT_PREEMPT_HOWTO](https://rt.wiki.kernel.org/index.php/RT_PREEMPT_HOWTO)

Is a low latency/real time kernel perfect for sound and especially for  pulseaudio.

:guitar:

---

### Post by Starks on 2010-05-12
Is it something that the average joe should care about or is it something that only mixers and sound editors should care about?

---

### Post by plun on 2010-05-12
> **Starks said:**
> Is it something that the average joe should care about or is it something that only mixers and sound editors should care about?

Well... ask Lennart Poettering, PulseAudios main man....:guitar:

He has expressed his opinion several times about Ubuntu and kernels..:redface:

---

### Post by ratcheer on 2010-05-12
> **zika said:**
> No Maverick branch on ricotz ppa, yet. Open Software sources, highlight ricotz ppa, edit maverick into lucid and remember to revert once Maverick branch is available...

Ok, thank you.

Tim

---

### Post by ratcheer on 2010-05-13
> **zika said:**
> No Maverick branch on ricotz ppa, yet. Open Software sources, highlight ricotz ppa, edit maverick into lucid and remember to revert once Maverick branch is available...

Well, I tried that but it didn't work, for me. It accessed the repository and offered me eleven new packages, which I declined, but the ricotz kernel was not among them. I am baffled.

BTW, a new kernel is being released, today, but the last time I looked, it was still building. [https://launchpad.net/ubuntu/maverick/+source/linux/2.6.34-2.8](https://launchpad.net/ubuntu/maverick/+source/linux/2.6.34-2.8)

Tim

---

### Post by zika on 2010-05-13
> **ratcheer said:**
> Well, I tried that but it didn't work, for me. It accessed the repository and offered me eleven new packages, which I declined, but the ricotz kernel was not among them. I am baffled.

BTW, a new kernel is being released, today, but the last time I looked, it was still building. [https://launchpad.net/ubuntu/maverick/+source/linux/2.6.34-2.8](https://launchpad.net/ubuntu/maverick/+source/linux/2.6.34-2.8)

TimGo to Synaptic, choose (from ricotz) 2.6.34, select linux-image***, linux-headers (2 files), and install...

---

### Post by ratcheer on 2010-05-13
Excellent. That worked, so I guess I am on "real" Maverick, now. Thank you.

Tim

---

### Post by jsevi83 on 2010-05-15
Ricotz, what is the difference between kernel 2.6.34rc7 in your ppa and the one in kernel-ppa/mainline? Which one should I use in lucid 64?

---

### Post by screaminj3sus on 2010-05-16
> **jsevi83 said:**
> Ricotz, what is the difference between kernel 2.6.34rc7 in your ppa and the one in kernel-ppa/mainline? Which one should I use in lucid 64?

I just installed this ppa and it also has a generic one. It works a bit better than the rc7 from the mainline ppa because the mainlineone would spam errors at boot saying stuff like "soft reset failed (device not ready)" and then ureadahead would crash. this one doesnt do that.

---

### Post by Peter09 on 2010-08-10
What has happened to this ppa: it seems to be static.

---

### Post by Finalfantasykid on 2010-08-11
Yes I would really like to know.  The jhbuild does not work on my install of Lucid, and would like to see how gnome shell is progressing.

---

### Post by cariboo on 2010-08-11
It's summer time in the northern hemisphere, devs take holidays too.

---

### Post by VastOne on 2010-08-11
Just to be sure, this shows up in Grub as 2.6.35.9-Generic, correct?

---

