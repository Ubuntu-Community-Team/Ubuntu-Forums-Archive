---
title: "[SOLVED] Can you enable Hibernation on an iMac?"
date: 2008-07-27
forum: Mac OSX
---

### Post by the8thstar on 2008-07-27
Hi all,

I went to the Apple Store the other day and I asked the vendor to try something for me, since I was unsure about the Sleep function on the iMac.

Basically, I wanted to know if Sleep put the iMac into Hibernation or just in Suspend mode. So he went ahead, opened a couple of apps, pushed "Sleep" and then unplugged the iMac as I requested.

When he turned it back on (after plugging it back in of course), the iMac rebooted and nothing had been saved. 

So... Sleep doesn't grant Hibernation on the iMac. So how can it be enabled like in XP, Vista and Ubuntu???

Thanks, 

the8th

---

### Post by bashveank on 2008-07-27
sudo pmset -a hibernatemode <1 for hibernate><0 for sleep>
It also hibernates automatically when you get into low battery, sleeping or not.

[smartsleep.prefane]("http://www.jinx.de/SmartSleep.html") can do it through the System Preferences gui

---

### Post by handy on 2008-07-28
> **bashveank said:**
> sudo pmset -a hibernatemode <1 for hibernate><0 for sleep>
It also hibernates automatically when you get into low battery, sleeping or not. 

The iMac ***is*** a desktop computer?

---

### Post by the8thstar on 2008-07-28
It is a desktop, not a laptop. Hibernation should work, shouldn't it?

[IMG]http://www.letsgodigital.org/images/artikelen/64/apple-imac-computer.jpg[/IMG]

I am wondering why you need to fiddle with the command line to enable Hibernation on Mac. That's very un-Mac.

---

### Post by bashveank on 2008-07-28
Ah, misread the post, sorry. the command should still work though.

> **the8thstar said:**
> I am wondering why you need to fiddle with the command line to enable Hibernation on Mac. That's very un-Mac.

Actually it's quite Apple-like: the stuff they let you do is easy, the stuff they think you don't care about is near impossible if you don't know what you're doing.

---

### Post by handy on 2008-07-28
> **bashveank said:**
> 
Actually it's quite Apple-like: the stuff they let you do is easy, the stuff they think you don't care about is near impossible if you don't know what you're doing.

The above sounds about right to me.

I'm an iMac owner too.  It goes to sleep on a timer or when you give the power button a short push.  

It seems to me quite unusual that someone would want to treat an iMac as though it was a notebook?

---

### Post by the8thstar on 2008-08-02
> **handy said:**
> The above sounds about right to me.

I'm an iMac owner too.  It goes to sleep on a timer or when you give the power button a short push.  

It seems to me quite unusual that someone would want to treat an iMac as though it was a notebook?

Not in the least. If there's a power outage and the iMac is asleep (not hibernating) all the work would be lost. With hibernation, it wouldn't be lost. This a MAJOR difference and a huge advantage for hibernation over sleep.

Anyway, would you be kind enough to run the command:

> sudo pmset -a hibernatemode 


<1 for hibernate><0 for sleep> as bashveank suggested? I'd like to know if this works or not.

---

### Post by bashveank on 2008-08-02
Useful tidbit that I just learned about: sudo pmset -a hibernatemode 3 will turn on 'safe sleep' and save the RAM contents to the HDD like it's about to go into hibernation, but then do a normal sleep. So if power is interrupted it can still resume.

---

### Post by handy on 2008-08-02
> **bashveank said:**
> Useful tidbit that I just learned about: sudo pmset -a hibernatemode 3 will turn on 'safe sleep' and save the RAM contents to the HDD like it's about to go into hibernation, but then do a normal sleep. So if power is interrupted it can still resume.

That does sound useful.

---

### Post by the8thstar on 2008-08-03
Yay, now I feel like it's more worthwhile buying a Mac... I just need a little bit o' money! ;)

On a more serious note now, the '3' option seems to be the most sensible. Why is it not the default? Is it because it takes a long time? Would the owner of a iMac be able to tell me?

---

### Post by bashveank on 2008-08-03
It was the default on my Macbook Pro. I think it does take slightly longer than a normal sleep though.

---

### Post by x0as on 2008-08-03
Was the default on my macbook as well.

---

### Post by handy on 2008-08-06
Oh! My God (which is actually most likely not the same God that you think owns you.) 

Anyway, God stuff aside, what else do we have in common?  Sorry, bad joke, well it is only a joke for those in the know.

So, I guess it is probably somewhat near impossible to imagine an entity that incorporates all of the manifest universes & all of the infinite potential as well.

AND, to talk of this any further is an absolute waste of time... Sorry!

Oop's sorry, I said God stuff aside... Oh well.

---

### Post by handy on 2008-08-07
Sorry, last night I was feeling particularly spiritual...  

To say the least! :lolflag:

---

### Post by the8thstar on 2008-08-07
You know, OMG Pink Ponies is the perfect place for you.

---

### Post by handy on 2008-08-07
> **the8thstar said:**
> You know, OMG Pink Ponies is the perfect place for you.

Not as perfect as it used to be I'm sorry to say... :lolflag:

---

