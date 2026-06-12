---
title: "Getting the microphone to work in Lucid Lynx"
date: 2011-06-13
forum: Multimedia Software
---

### Post by Very Lucid Lynx on 2011-06-13
Hi,

I've had trouble getting the microphone to work already with Hardy Heron, but especially now with LL I've tried a lot of things and they don't seem to help. I have used the mike successfully in Windows 7 very recently so it isn't broken.

I have **Ubuntu 10.04.2 LTS**, and a **SoundBlaster Audigy 2 Platinum** soundcard. For other system details, I don't know the Terminal command.

I'm also still a relative newbie, especially when it comes to using the Terminal.

Here is a list of things I've tried, based on what I've found from Google:
[COLOR=Red]
**[SIZE=2][COLOR=DarkRed]1.[/COLOR][/SIZE]**[/COLOR] Un-muted the microphone settings from System->Preferences->Sound->Input, and from Gnome Alsa Mixer and from the older Alsa Mixer.

**[SIZE=2][COLOR=DarkRed]2.[/COLOR][/SIZE] **Tried different combinations (mic 1, mic 2, etc.) from System->Preferences->Sound->input.
[SIZE=2]
**[COLOR=DarkRed]3.[/COLOR]**[/SIZE] Changed various volumes from the Gnome Alsa Mixer.

Despite these attempts, Sound Recorder couldn't even start recording.

[SIZE=2]**[COLOR=DarkRed]4.[/COLOR]** [/SIZE]Started the alsamixer directly from Terminal (the one that is operated on keyboard only), and then tried changing various volumes from there.

I think after this step, I could get Sound Recorder to start recording, but it just recorded nothing. And also, I could start to hear the microphone from my speakers, even though I wasn't able to record anything, and I could just hear it when I tapped the microphone etc.

[SIZE=2][COLOR=DarkRed]**5.**[/COLOR] [/SIZE]installed PulseAudio Volume Control, and on the Input Devices tab, tried putting the left channel at zero, or the right channel at zero. (This is an advice some people have offered for getting Skype to work.)

At some point, I got to the present situation, where Sound Recorder does record, but the result is just a crackling noise that gets recorded whether I am close to the microphone at all or not.

So it seems I've messed up some of the Alsa settings probably, and they did work better at an earlier point.

I have also updated the Alsa to a slightly newer version (something ending in .23 I think?).


Any help will be much appreciated, thanks.

---

### Post by lidex on 2011-06-18
[http://ubuntuforums.org/showpost.php?p=10784896&postcount=38](http://ubuntuforums.org/showpost.php?p=10784896&postcount=38)

---

