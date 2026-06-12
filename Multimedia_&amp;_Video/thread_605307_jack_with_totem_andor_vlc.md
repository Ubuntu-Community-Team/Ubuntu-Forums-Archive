---
title: "jack with totem and/or vlc?"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by battles33 on 2007-11-06
alrighty, so i've made the post in a different forum (Installation & Upgrades), but since the question's a multimedia related question i'll ask it here (hopefully it's alright to ask the same question twice, please forgive if not)

links to the files i refer to in this can all can be found in my post in that Installation & Upgrades forum

i've been searching for help with setting up vlc and/or totem (as well as sound juicer) so that these programs have their audio output sent to jack (i've upgraded the regular 7.10 installation to ubuntu studio and am using the computer for both studio work and all-around stuff). i was finally successful in figuring out vlc as i had found an rpm with vlc-plugin-jack that could then be installed in ubuntu with a program called alien (why is this plugin not listed normally in the repository?????!???!!!) it's working like a charm.

so, i also found a jack plugin for gstreamer (also not in the repositories, have to "alien" another RPM file). installed gstreamer and the jack plugin, made sure totem-gstreamer was installed rather than totem-xine. however, no luck. i guess it'll be a simple command to run from the terminal or something, however i have not yet figured it out. if anyone knows how to get this last step working, i'd appreciate it so much (and along with it, to configure sound juicer to do the same. sound juicer's not really important but it'd be nice to have it also going through jack).

---

### Post by kd7swh on 2007-11-07
As you know Ubuntu doesn't ship with jack or vlc installed and the copy of vlc in the repos. doesn't support jack but if you compile vlc you can just use the --enable-jack command when you configure it. You don't need a plug-in. If you compile totem from source this maybe an option too i don't know.

---

### Post by battles33 on 2007-11-07
so vlc doesn't appear in the repos to install? i apologize, and also have no idea how i in fact ended up installing it then. that's what happens when you've been working with too many programs lol. i had assumed that when you search vlc in synaptic that it will appear

i guess with the studio upgrade/install the jack associated packages appear in synaptic. so i guess it'd be a matter of contacting the ubuntu studio team to inform them they are missing some helpful and important plugins for the studio install?

---

### Post by Stochastic on 2007-12-19
> **kd7swh said:**
> As you know Ubuntu doesn't ship with jack or vlc installed

UbuntuStudio (which battles33 had said he has) does infact ship with jack installed.

---

