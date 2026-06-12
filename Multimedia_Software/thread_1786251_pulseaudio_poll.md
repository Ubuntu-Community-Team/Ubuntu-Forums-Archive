---
title: "pulseaudio poll"
date: 2011-06-19
forum: Multimedia Software
---

### Post by rsteele1 on 2011-06-19
has anyone gotten pulseaudio to work out of the box on a new install?ive been using ubuntu since v6.when pulse became default sound i have had nothing but trouble.system sounds dont even play.it seems to me that something as basic as system sounds should work in a new installi see a lot of advice on how to config things to get sound working.and a lot of excuses.
pulse started as default in v8.04.were up to v11 now.how long is it going to take to fix this problem?4 versions with the same basic issue?

---

### Post by kostkon on 2011-06-19
Actually, 80% or more of the audio problems are alsa related, but people tend to blame pulseaudio anyway.

What problems do you have?

---

### Post by amauk on 2011-06-19
Have you filed bug reports, etc.

If it's some corner-case bug that depends on a specific hardware setup / config and you don't, then it's not going to get fixed as no-one else is aware of the problem

---

### Post by rsteele1 on 2011-06-19
no i havent filed a bug report.im sure the developers are aware that there are problems with pulse not working out of the box.
second-this happens on every distro o have tried and on every machine i have tried.thought it might be the iso dowload corrupt.but i have done multiple downloads and used up a 50 pack of dvds.
i dont see how the problem is alsa related when pulse is the sound server.and the problems dont manifest on older distros without pulse.
bottom line....pulse isnt implemented properly in ubuntu and it needs to be taken out untill it is fixed

---

### Post by rsteele1 on 2011-06-19
from wikipedia

"When first adopted by the distributions, PulseAudio developer [Lennart Poettering]("http://en.wikipedia.org/w/index.php?title=Lennart_Poettering&action=edit&redlink=1") described it as "the software that currently breaks your audio".[[6]]("http://en.wikipedia.org/wiki/Pulse_audio#cite_note-5") Poettering later claimed that "Ubuntu didn't exactly do a stellar job. They didn't do their homework" in adopting PulseAudio[[7]]("http://en.wikipedia.org/wiki/Pulse_audio#cite_note-6") for [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29") "Hardy Heron" (8.04), a problem which was then improved with subsequent Ubuntu releases.[[8]]("http://en.wikipedia.org/wiki/Pulse_audio#cite_note-7") However, on October 2009, Poettering reported that he was still not happy with Ubuntu's integration of PulseAudio.[[9]]("http://en.wikipedia.org/wiki/Pulse_audio#cite_note-8")"

---

### Post by amauk on 2011-06-19
File a bug report and get your issue fixed.
Complaining on a forum won't fix your issue

---

### Post by rsteele1 on 2011-06-19
if you had looked you would see this thread is a poll. not a complaint.also see my quote from the pulse developer.the facts speak for themselves

---

### Post by rsteele1 on 2011-06-19
so far no one has posted that they had pulseaudio working out of the box(by that i ment after a clean install) so i went to launchpad and searched "pulseaudio no sound after install"
search returned:
1  &#8594; 20  of [SIZE=3]_**26700 pages **_[/SIZE]matching "pulseaudio no sound after install" 
seems a bit too many for something that is supposed to be the greatest sound server and fix so many "problems"

---

### Post by amauk on 2011-06-19
it's 'cause we can't see your poll
none of us can get xorg working either

---

### Post by beew on 2011-06-19
> **rsteele1 said:**
> has anyone gotten pulseaudio to work out of the box on a new install?ive been using ubuntu since v6.when pulse became default sound i have had nothing but trouble.system sounds dont even play.it seems to me that something as basic as system sounds should work in a new installi see a lot of advice on how to config things to get sound working.and a lot of excuses.
pulse started as default in v8.04.were up to v11 now.how long is it going to take to fix this problem?4 versions with the same basic issue?

Yeah, it always works great out of the box. I am constantly baffled by people complaining about pulse. I have never experienced any problem with it and I have installed/test Ubuntu on random machines with different specs.

But then I have started using Ubuntu only since 10.04 so maybe people have experienced problems before, somehow the memory sticks even though pulseaudio may have vastly improved since. One time I have an issue with 10.04 and I posted a thread on the forum, some guy immediately told me I should uninstall pulseaudio, not knowing better I went ahead, the problem wasn't solved but sound quality has gotten worse. I reinstalled it and the sound improved. I think people may be blaming pulse for unrelated issues or because they have old crappy hardware.

BTW, I don't do upgrade, always clean install.

P.S. I don't see any poll either, I think you can only make polls in the Ubuntu forum cafe.

---

### Post by desnaike on 2011-06-19
Pulseaudio has always worked for me since it's inception.

---

### Post by phz_swe on 2011-06-19
I have manually and willingly installed PulseAudio on my main Debian computer after getting experience with it on Ubuntu. I think Pulse is a great concept, not least the network transparency. It also seems to have made itself a standard quite quickly (many programs offer PulseAudio output, without the old ALSA emulation layer).

That is my experience, of course other people have others.

---

### Post by gordintoronto on 2011-06-19
On my current desktop, sound in and out have worked "out of the box" in 10.04, 10.10 and 11.04. "Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)"

On my laptop, sound worked fine with a headset but not with the internal speakers in 10.04. In 10.10 and 11.04, (tested by booting from a flash drive) it has worked "out of the box."

I know some people find their sound output, or microphone input, is muted after installation. I have no idea why.

---

