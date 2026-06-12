---
title: "Audacity playback &quot;error while opening sound device&quot;"
date: 2008-02-28
forum: Multimedia Production
---

### Post by Zeikcied on 2008-02-28
I'm trying to use Audacity to edit an existing MP3 file.  I'm not recording anything.

The MP3 is actually two songs in one (Jonathan Coulton's covers of We Will Rock You and We Are The Champions, purchased from his site), and I'd like to split them.

I attempt to play the file about halfway through, just to be sure of where the first song ends and the second starts.  But I get the "Error while opening sound device" message.  Or Audacity plays a split second, freezes, and refuses to respond.

I've searched the forums, and all I'm finding are people getting the error on recording attempts, and not playback.  I'm only attempting to play, not record.

The Playback menu only has "ALSA: default" and "ALSA: dmix," neither of which work.  The Recording menu has "OSS: /dev/dsp," "ALSA: ATI IXP: ATI IXP AC97 (hw0,0)," and "ALSA: default."  Setting Recording to either ALSA does not work.

It might be worth noting that the MPlayer plugin for Firefox can connect to ALSA, but for some reason stopped connecting to OSS sometime in the past few weeks.  If that's in any way relevant.

Do I need to install something?  I just tried reinstalling Audacity, and that did not work.

---

### Post by heffo_j on 2008-02-29
Yep,

I have the same problem. It is the new upgrade 1.3.4 (I think). It does not boot properly for me either. Sound playback error message the same as you have. 

There is a serious problem somewhere. I went to the Linux Mint Software Portal and installed the 1.3.3 and it works fine again.

My guess is that something is not being cleaned up properly in the upgrade and it is cause these lock ups and crashes. 

Solution: go back and reinstall 1.3.3.

Regards
John

---

### Post by sceo on 2008-04-17
Yeah, just wanted to confirm that when I reverted to 1.3.3 by uninstalling Audacity 1.3.4 through Synaptic, then installing 1.3.3 from [http://packages.ubuntu.com/gutsy-updates/i386/audacity/download](http://packages.ubuntu.com/gutsy-updates/i386/audacity/download) everything went back to "working."  So what's wrong with 1.3.4 in Gutsy?

---

### Post by faust99 on 2008-04-22
I couldn't get playback either so had to downgrade as well. It works again now... \\:D/

---

### Post by viljun on 2008-04-27
Solution: Just kill jackd.

1) ps -e|grep jackd
2) check the process id (it's the first number on the line for example 9466)
3) sudo kill 9466

Jack will restart every time you boot your machine - until it's (hopefully) fixed. So you have to do this every time.

---

[Mooble]("http://www.mooble.fi") [Varuste.net]("http://www.varuste.net") [Frakkipalvelu NAM]("http://www.frakkipalvelunam.fi")

---

### Post by viljun on 2008-04-27
> **viljun said:**
> Jack will restart every time you boot your machine - until it's (hopefully) fixed. So you have to do this every time.

In fact jackd is restarted every time you launch audacity. So, first start audacity and then kill jackd in console.

---

### Post by mariodavidpalacio on 2008-04-29
THANK YOU
THANK YOU
THANK YOU


I was getting that awful message every time I tried to do something with my Audacity (Ubuntu 7.10) and the solutions was here.

For those who are getting it when trying to record or playback something: DOWNGRADE to Audacity 1.3.3 and it will work as it should (it worked for me).

[http://packages.ubuntu.com/gutsy-updates/i386/audacity/download](http://packages.ubuntu.com/gutsy-updates/i386/audacity/download)

---

### Post by ignasigarcia on 2008-05-11
unless you need jackd for any reason, uninstall it by doing apt-get purge jackd. that'll do the trick

cheers

ignacio

---

### Post by 4ebees on 2008-05-12
Hey Matey,

Thanks for the solution. Worked first time (and second...and third :)))

Much appreciated.


> **viljun said:**
> Solution: Just kill jackd.

1) ps -e|grep jackd
2) check the process id (it's the first number on the line for example 9466)
3) sudo kill 9466

Jack will restart every time you boot your machine - until it's (hopefully) fixed. So you have to do this every time.

---

[Mooble]("http://www.mooble.fi") [Varuste.net]("http://www.varuste.net") [Frakkipalvelu NAM]("http://www.frakkipalvelunam.fi")

---

### Post by ironss on 2008-07-23
Rather than killing jackd after starting Audacity, or uninstalling jackd, you can do one of three things:

* make jackd work properly
* make jackd use a dummy sound card or
* prevent jackd from starting entirely

They all involve a file called /etc/jackdrc (if you want to do this for all users) or ~/.jackdrc (for a single user), which contains a command for starting jackd


Making jackd work properly is too difficult to describe here.


To make jackd use a dummy sound card, jackdrc should contain a line something like:

/usr/bin/jackd     -T -d dummy -C 2 -P 2 -r 48000 -p 128

jackd will drive a pretend sound card with two inputs (-C 2) and two outputs (-P 2) at 48000 samples per second. You have to set your Audacity project sample rate to match this, otherwise you get the 'error while opening sound device'.


To prevent jackd from starting, jackdrc should contain an illegal command; you can try adding a # to the front of the line above:

#/usr/bin/jackd     -T -d dummy -C 2 -P 2 -r 48000 -p 128

Then jackd will not start and you will have access your ALSA and OSS sound card.

Note, however, that if you have any other applications (Totem, Rhythmbox) actually USING the sound card, then Audacity will not be able to use it and you will still get the 'error while opening sound device'.

---

