---
title: "Google Voice &amp; Pidgin- ALMOST there!"
date: 2010-09-17
forum: Multimedia Software
---

### Post by mathewd on 2010-09-17
Hello all,

Ive run into some trouble using Google Voice with Pidgin. I have it so  that, when someone calls my Google Voice number, it will ring through to  Pidgin via Google Talk support. I get a pop-up notification of the  incoming call, and I click accept.

At this point Pidgin opens the conversation but Google Voice asks me  over the speaker to "Press 1 to accept, Press 2 to send to voicemail"  and since Pidgin has no DTMF pad, I cannot do either and the call  eventually disconnects.

How can I send DTMF tones? I tried installing dtmfdial from the  repositories, but it only works when the soundcard is not already in  use. So it will generate the tones up until Pidgin accepts the call, but  then once the call is "connected" (and I get the request to press 1 or  2), dtmfdial ceases to work. Is there a way to fix this?

By the way, I have tried altering Google Voice preferences so that I  dont receive that message, but no luck. Their option to "turn off call  screening" only eliminates the name-screening feature. Others find this  annoying too; especially those with bluetooth devices. So I think  attacking the problem from this angle won't work. 

Thanks for your help!

---

### Post by dmar198 on 2010-09-17
> **mathewd said:**
> Hello all,

Ive run into some trouble using Google Voice with Pidgin. I have it so  that, when someone calls my Google Voice number, it will ring through to  Pidgin via Google Talk support. I get a pop-up notification of the  incoming call, and I click accept.

At this point Pidgin opens the conversation but Google Voice asks me  over the speaker to "Press 1 to accept, Press 2 to send to voicemail"  and since Pidgin has no DTMF pad, I cannot do either and the call  eventually disconnects.

How can I send DTMF tones? I tried installing dtmfdial from the  repositories, but it only works when the soundcard is not already in  use. So it will generate the tones up until Pidgin accepts the call, but  then once the call is "connected" (and I get the request to press 1 or  2), dtmfdial ceases to work. Is there a way to fix this?

By the way, I have tried altering Google Voice preferences so that I  dont receive that message, but no luck. Their option to "turn off call  screening" only eliminates the name-screening feature. Others find this  annoying too; especially those with bluetooth devices. So I think  attacking the problem from this angle won't work. 

Thanks for your help! All you need to do is more carefully adjust your Google Voice settings. When you are on the settings page, click the Calls tab. There, under the heading "Call Screening," there should be three ticker-boxes: first, an "On" ticker box, then, below it, an indented, second, sub-ticker box offering the option to "Ask unknown callers to say their name." Then there's the THIRD box, which is just plain "Off." Make sure that BOTH 1 and 2 boxes are de-clicked, then select "Off." You should no longer have any vocal previews of your callers; they should just go straight through. At least, that's how it works on my system.

---

### Post by mathewd on 2010-09-18
thanks for the reply dmar.

sadly, i double-checked my settings, and they are already exactly as you suggested. When it is ""On" it simply tells me who is calling, then asks if i want to answer or send to voicemail. In the current "Off" settings, it no longer tells me who is calling (no vocal previews) but still demands that I press 1 or 2. Like i mentioned, based on the google voice help forums, it seems a lot of people have this problem.

 I think my problem could be solved by getting those darn DTMF tones to play! i had hoped to map a keyboard shortcut to the command "dtmfdial 1" but of course it wont work with the soundcard in use. i wish i were smart enough to figure out how to get around that lol.

---

### Post by peter72 on 2010-09-21
I still have the same issue.  I've went so far as to download a DTMF mp3 file of the number 1 and try playing it back through the microphone.  Still no luck of course.  I tried the dtmfdial app, but had no luck (/dev/dsp is busy).  Need to really get this added to pidgin, as if you're calling a bank or something, it would be nice to have it to enter in your account number etc.

---

### Post by mithereal on 2010-10-30
i agree i am havung the same error with gogle asking me to press 1, has anyone found a solution
im usinging pidign 2.6.6

---

### Post by DinkyDogg on 2010-12-22
Bumping this thread -- still no solution, as far as I know.

---

### Post by Xanko on 2010-12-30
Interesting, I am looking for a way to accept my Google Voice calls aside from having to search for my gmail tab. Might have to check this out once its fixed.

---

### Post by argentum2f@gmail.com on 2011-01-03
I've been looking all day, and can't find anyway around this. Seems like a simple to overcome problem though. Part of the problem seems to be on google's end for asking even when screening has been turned off. If the pidgin developers could add in touchtone functionality that would be great.

In the mean time, is there anyone who knows more about how the audio works in linux who could suggest a way to mimic a dialtone on the mic input or something useing  dtmfdial or a recorded dialtone?

EDIT: Has anyone gotten any other programs to work like this? I've tried empathy, psi and some others, but they don't even register that someone is calling, though chat and video chat seem to work.

---

### Post by Consecrated on 2011-01-19
Have you successfully linked "Google Voice" and "Google Talk?" Can your calls come in through "Google Talk" (not the Gmail utility)?

Does anyone know of a Gnome Panel plug in that has the same features as the Google Voice plug in for the Google Chrome browser? I would like some sort of widget to text people from my Google Voice account and receive Ubuntu notifications when I get texts, possibly through empathy or an IM client.

---

### Post by obadz on 2011-02-06
As folks mentioned, it's problematic that GVoice refuses to disable call screening on GTalk ([http://www.google.com/support/forum/p/voice/thread?tid=57aad182bcb85d63&hl=en&fid=57aad182bcb85d6300049ba897561b9f](http://www.google.com/support/forum/p/voice/thread?tid=57aad182bcb85d63&hl=en&fid=57aad182bcb85d6300049ba897561b9f)) but I think we'll really need a dialpad in pidgin even if they do fix it (think about what happens you call your bank and the automated teller asks you to "press 2 for balances").

There seems to be a patch floating out there for the underlying library ([http://developer.pidgin.im/ticket/12617](http://developer.pidgin.im/ticket/12617)) but it's not clear if it works and no GUI has been linked to it.

There's another ticket on the same topic: [http://developer.pidgin.im/ticket/12828](http://developer.pidgin.im/ticket/12828)

---

### Post by topgun98 on 2011-04-02
::bump::

I'm having the same issue.  I'll pay someone to build a dial pad for pidgin, if anyone knows how.

---

