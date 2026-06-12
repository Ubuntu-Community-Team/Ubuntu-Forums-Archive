---
title: "Skype version spoofing (howto stick with your old skype version)"
date: 2014-08-23
forum: Multimedia Software
---

### Post by martinr on 2014-08-23
_Context_

If you are running Skype on Linux and didn't upgrade to the new version 4.3.0.37, then as of august 2014 you can't login any more and get the message:
> "Skype can't connect." 
or 
"Skype can't login."
or 
"We've signed you out because you're using an outdated version of Skype. Download the latest version now."
M$ claims that forcing users to drop 4.2 and move to 4.3 improves their lives and makes their Skype experience better.
(source: [Community Skype]("http://community.skype.com/t5/Linux/Having-trouble-signing-in-Retirement-of-older-versions-of-Skype/td-p/3439685"))


_Problem_

Not all people can upgrade because they're on an older Linux version that is not supported by the new Skype version. 
The new Skype version also introduces all sorts of new problems to existing users, as the following posting illustrates:
[QUOTE="JGipsz"]
Skype 4.3:

    Crashes with previous chat history, but if you remove it and have been talking a lot, it takes years for you to be able to actually use Skype due the fact that it downloads ALL YOUR PREVIOUS chat history.
    It forces you to use PulseAudio, so basically sound is not working properly, microphone doesn't work and so on. It's not as if I'm going to use PulseAudio anyway. Honestly, how hard could it have been to just not drop ALSA support?
    Camera is not working either. Yay.
    Screen sharing is not working either.
    Ugliest UI I've seen in my whole life. Those giant useless buttons at the top are just irritating. It makes the window 10% larger, and the empty spaces are ugly. In 4.2, there were small icons at the bottom left which was just perfect.

I want to use Skype, but stop forcing us to use 4.3, especially because it is broken. Why do you force us to use something that is broken? Why ruin something that has been working flawlessly? 4.3 has no bugfixes, it introduces more bugs instead. It kind of reminds me of Mojang, to be honest.
[/QUOTE]
See for a full description of complaints the thread at: [Community Skype Linux forum]("http://community.skype.com/t5/Linux/Having-trouble-signing-in-Retirement-of-older-versions-of-Skype/td-p/3439685/page/4") (warning 19 pages of them)
See also the article at: [Disruptive Telephony - The community outrage, by Dan York]("http://www.disruptivetelephony.com/2014/08/why-is-skype-forcing-a-software-upgrade-on-all-of-us-plus-the-community-outrage.html")


_Solution_

You can stick with your old version of skype. I came across and tested (on Skype 4.2 on Ubuntu LTS 12.04) the following solution that spoofs your old version of Skype  to version 4.3.0.37. The command below will output a replace command which you could copy and run in a terminal in order to change the version string in your old Skype executable. Your old Skype will then be allowed to connect again to the M$ server. First you have to fill in your current Skype version in the command below, which can be obtained with command: "skype - version".
```

ver=$(echo "4.2.0.11" | xxd -p | sed 's/.\{2\}/&\\x/g;s/^/\\x/;s/\\x0a\\x//'); echo "sudo sed -i \"s/$ver/\x34\x2E\x33\x2E\x30\x2E\x33\x37/g\" /usr/bin/skype"

```
Credits for this solution go to: [MikeLinux @ unix.stackexchange]("http://unix.stackexchange.com/questions/148076/skype-version-spoofing") also known on this forum as [MikeTheC]("http://ubuntuforums.org/member.php?u=378984")

Enjoy it while it lasts. Furthermore you might be on the lookout for a more secure alternative. I can Imagine they will try to block this solution in the future.

---

### Post by martinr on 2014-09-20
Version Spoofed Skype 4.2.0.11 suddenly stopped working again.
I had locked the Skype version in Synaptic to 4.2.0.11, but in an instance I saw skype-bin flash by during the routine update from the package manager.
Something was messed up because Skype suddenly refused connecting again.

Does anybody know what's changed?

Was Skype in the repository messed up?
Has the Skype/M$ Server side been tightened up again?
Has the version spoofed Skype stopped working for other people as well?

---

### Post by geestbos on 2014-09-20
I confirm, the spoofing workaround for 4.2.0.11 does not seem to work. I cannot say 'any longer' since I only tried it out just now. I can say that it's likely not linked to unwanted updates from your package manager, since I re-installed Skype 4.2 this morning based on a older .deb installation package (skype-ubuntu-precise_4.2.0.11-1_i386.deb; 7/5/2013). So I guess that's the end of Skype on this PC (~ SSE2 unsupported).

---

### Post by rusty-robot on 2014-09-20
Yes martinr, spoofed Skype 4.2.0.13 stopped working for me as well. Looking for workaround again...

UPD: I had to move to Skype 4.3 + [apulse wrapper]("https://github.com/i-rinat/apulse")

---

### Post by Alai_Mac_Erc on 2014-09-30
I've tried a number of fixes for this under crouton/Ubuntu 12.04 on an Acer C720.

Pulseaudio seems to be very unstable.  Works for a while, then starts to die (or at least, produce no speaker sound) on desktop switch.

apulse ([https://github.com/i-rinat/apulse](https://github.com/i-rinat/apulse)) doesn't appear to produce any sound whatever.  No diagnostic messages at all, just runs silently (in both senses).

However, logging into skype-4.3, quitting *without logging out* and then uninstalling and downgrading to 4.2 does appear to work.  (At least for now.)

---

### Post by jefelex on 2014-10-01
Micro$loft doesn't like competition, just they just poison anything that they have to produce that may be used by another OS. I knew it was the beginning of the end when Skype was purchased by MS - too bad actually, Skype was a good product.

---

