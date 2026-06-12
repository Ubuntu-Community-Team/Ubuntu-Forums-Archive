---
title: "Does audio ever work on Ubuntu?"
date: 2011-10-10
forum: Multimedia Software
---

### Post by Alastair Rae on 2011-10-10
Browsing this forum I see lots of unanswered queries from people (myself included) with various sound problems. At the top are two stickies, one of which appears not to have been updated for five years.

So this forces the question, does simple audio ever work out of the box? Or is it always necessary to uninstall/install/reinstall a bunch of non-obvious packages and rebuild kernel modules?

If it doesn't work out of the box, I assume that most users just don't bother with things like Skype because they're just too hard to get working.

---

### Post by haqking on 2011-10-10
> **Alastair Rae said:**
> Browsing this forum I see lots of unanswered queries from people (myself included) with various sound problems. At the top are two stickies, one of which appears not to have been updated for five years.

So this forces the question, does simple audio ever work out of the box? Or is it always necessary to uninstall/install/reinstall a bunch of non-obvious packages and rebuild kernel modules?

If it doesn't work out of the box, I assume that most users just don't bother with things like Skype because they're just too hard to get working.

simple answer is depends on your hardware i guess.

I have never had a single issue with sound in any distro to be honest.

I am currently running 10.10 and debian stable and sound works fine.

---

### Post by SeijiSensei on 2011-10-10
Skype problems often have more to do with choosing the correct microphone input.  Most every computer comes with a microphone jack on the motherboard, which is typically the default input.  If you have a webcam with its own microphone, as I do, you need to make the webcam's mike the default in pulseaudio.  How you do that depends on the flavor of Ubuntu you're using.  On Kubuntu, it's controlled by System Settings > Multimedia > Phonon.  Don't know about GNOME Ubuntu.

Sometimes one piece of the audio system has mute enabled.  I had that problem the other day, but it was the result of my playing around with pavucontrol and padevchooser.  By default, I always get sound out of the box, but I'm using the vanilla analog output on my motherboard.  Using an outboard card often requires specific drivers.

---

### Post by Alastair Rae on 2011-10-10
> **haqking said:**
> simple answer is depends on your hardware i guess.

I have never had a single issue with sound in any distro to be honest.

I am currently running 10.10 and debian stable and sound works fine.
I wonder if there are many difference in the audio handling in 11.04. Maybe I should try downgrading to a more stable release?

---

### Post by 2F4U on 2011-10-10
Sound works fine here on Xubuntu 11.04 and it worked on previous versions. So I guess it has more to do with the hardware than with the Ubuntu version.

---

### Post by haqking on 2011-10-10
> **Alastair Rae said:**
> I wonder if there are many difference in the audio handling in 11.04. Maybe I should try downgrading to a more stable release?

I have used a 11.04 Live CD and it works fine also.

It depends on your hardware, also as seiji said above skype is notorious for audio issues, which usually come down to the settings.

---

### Post by viperdvman on 2011-10-10
I've never had audio issues either out-of-the-box. The only thing I had to do on my desktop and netbook was go into my ALSA mixer settings in the Terminal (Konsole for KDE users) and adjust some of the capture settings so I could record from videos in Audacity.

Other than that, I've had nothing but great audio out-of-the-box. Note: Netbook has integrated sound, desktop has the top-of-the-line SB Audigy 2.

---

### Post by WasMeHere on 2011-10-10
I have also noticed quite a few threads about audio: microphone, loadspeakers or headset not working, and I think we have to admit, that it is not working out of the box often enough.

For me it is not a big problem, because I usually find where to tweak it, but it is not obvious for a new-comer to linux. Actually I think that Linux Mint (based on Ubuntu) works much better out of the box regarding audio as well as general multimedia playback. I also realize that the Ubuntu way of distribution with preinstalled systems on computers makes it impossible to bundle some proprietary software without a license fee, while Mint is only distributed directly to the end-user.

Have fun finding the correct settings
Olle

---

### Post by dFlyer on 2011-10-10
> **Alastair Rae said:**
> Browsing this forum I see lots of unanswered queries from people (myself included) with various sound problems. At the top are two stickies, one of which appears not to have been updated for five years.

So this forces the question, does simple audio ever work out of the box? Or is it always necessary to uninstall/install/reinstall a bunch of non-obvious packages and rebuild kernel modules?

If it doesn't work out of the box, I assume that most users just don't bother with things like Skype because they're just too hard to get working.

Yes, it works out of the box depending on your hardware.

---

### Post by oldsoundguy on 2011-10-10
Nary a major issue with audio on my equipment.  BUT, I use desktops, not a laptop.  Began using Ubuntu with v6.04.  Only issue has been using the digital out on the card(s).  That does not work most of the time.  Analog has never failed.

Skype .. that is a problem!  Drivers are old and many times I have been unable to run even the test function as it will not access my network.  PLUS, Skype is now owned by Microsoft, so drivers will be few and far between for any OS other than Windows.
I use VoIP instead .. but no video phone with it.

---

### Post by dFlyer on 2011-10-10
You might want to make sure your printer and sound card (if you have them) are not clashing on irq 5. That use to be a major problem years ago. Don't know if it's still a problem today.

---

### Post by JRV on 2011-10-10
Sound has worked out of the box on every Ubuntu installation I have ever done, going back to 7.04.

---

### Post by Tye on 2011-10-10
I am with you buddy, i have been using ubuntu since 4.10 and while it usually works out of the box as soon as I update thats when the trouble starts.

I am quite sick of it, i just converted my first user to ubuntu (the missus)
and i told her how easy ubuntu is to use.

Well i should have known better 

there was an update 5 days before 11.10 is released and I wondered why would they release an update so close to a dist upgrade?
well i upgraded anyway and Lo and behold the sound stops working, i dont know if thats what caused it but i am 99% sure based from past experience.


I am really really sick of spending the amount of hours i do on trying to get ubuntu working. I am not even going to bother to try and fix it. i am just gonna wait for the new 11.10. i know it will work (the sound) and i will just not update for a while.

---

