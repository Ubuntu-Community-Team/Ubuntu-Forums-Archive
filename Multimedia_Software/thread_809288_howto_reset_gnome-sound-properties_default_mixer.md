---
title: "howto reset gnome-sound-properties default mixer ?"
date: 2008-05-27
forum: Multimedia Software
---

### Post by suoko on 2008-05-27
Hi,

after I fixed my headphone problems with my asus A6F, I ended up with the oss-mixer as the only available mixer under gnome-sound-properties which behaves really bad: I can't modify volume now.

I tried creating a fresh new user and noticed I can choose between the oss-mixer AND the intel-hda-alsa-mixer for it.
How do i completely reset gnome-sound-properties (or alsa) values ?
I looked into gconf-editor but have no clue how to proceed.
Do I have to reset gstreamer values too?
I'd like not to remove all my gnome settings for my main user in order to solve this silly matter.
I also tried "asoundconf set-default-card Intel" command with no change.
I even removed all .asound files in my home.

thanks in advance

---

### Post by suoko on 2008-05-27
solve by enabling pulseaudio in gnome session startup programs (i didn't think it was necessary for alsa to work)

Then I set all input, output and mixer to pulseaudio in gnome-sound-properties.

Now headphones volume is very low (but it's probably better this way ;-)

---

