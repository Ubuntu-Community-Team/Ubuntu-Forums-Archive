---
title: "freenx -&gt; esound -&gt; pulseaudio"
date: 2009-03-10
forum: Multimedia Software
---

### Post by seppl82 on 2009-03-10
Hi all,

today i've tried to setup my remote sound due nxserver from a ubuntu hardy to a windows xp machine.

Therefore i've setuped the pulseaudio devices like described in the following tutorial...

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

My idea is to send all soundoutput to the pulseaudio server that sends the sound through esound to my nxclient.

Therefore i've installed additionally the package "pulseaudio-esound-compat"

After the setup i can't see any device in the PulseAudio Manager that tells me there is a esound client attached.

Did i've missed something?

It is very Paradox that i can hear the login sound of the ubuntu gnome if i logon, but anything sent to PulseAudio just appears on the local machine.

Kind Regards

Seppl

---

### Post by jedibrand on 2009-03-26
Hey, make that two of us.

I'm presently using NoMachine nxserver free, but am quite capable and happy to move to freenx if necessary.

I should also add that I do not have anything to contribute to this thread as of yet. I've installed and configured pulseaudio on Hardy Heron, but have yet to do any research on an esd plugin/wrapper/thingamagig.

Just to state my needs clearly, I'd like to be able to hear sound on a machine running NoMachine client (Mac OS 10.5, in this case) coming from a running NoMachine nxserver free (or freenx for that). Again, the server runs on Hardy, and my understanding is that NX will only stream audio via esd. So, would it be possible to use a plugging for pulseaudio in order to stream sound via from NX via esd? I might be a bit confused on the sound pathway here, so please correct me if I'm wrong!

Ultimately, I'd like to be able to play music on my Hardy server at home via Amarok (which I like to use, thanks to the fact that it makes it easy to browse my music/podcast/streams collection), pipe that through the nets, and then hear the sound from my Macbook, at work or elsewhere. And of course, I'm open to suggestions for alternative sound streaming/delivery methods.

---

### Post by markbuntu on 2009-03-26
According to the nomachine website they do not support Hardy or Intrepid. This is for good reason since ESD was dropped from those releases. You should bug them about pulseaudio support since pulse has replaced ESD. They will need to to support pulseaudio and rtp in any case since so many distros are moving to it. 

nxserver seems sort of overkill just for streaming audio anyway. Have you considered setting up an icecast server?

---

### Post by jedibrand on 2009-03-27
Thanks for the reply, Mark.

I have to agree with you. After I posted yesterday, I started thinking about the whole setup and it dawned on me that perhaps it's a bit cumbersome to begin with.

I have run an icecast server in the past, and I've had good experience with it. I think I mostly just wanted to be able to do everything via one process--i.e., NX, vs. running two separate remote desktop/audio setups, one for audio via icecast, another for remote desktoping via NX. Plus, it'd be nice to get sound on the local client coming from apps that I run through my NX sessions in general.

For now, though, I'm falling back on the icecast server. I'll post back if I do manage to get the [Amarok] -> PulseAudio -> ESD -> NX setup going.

---

### Post by abuster on 2010-10-15
Install paprefs on server and client:

```

sudo apt-get install paprefs

```

Open paprefs on client. Go to Network Server. Enable network access. Don't require authentication.

[IMG]http://www.seljebu.no/img/paprefs1.png[/IMG]

Open paprefs on server. Go to Network Access. Make discoverable PulseAudio network devices avaiable localy.

[IMG]http://www.seljebu.no/img/paprefs2.png[/IMG]

Reboot/new login not required.

Play your favorite music and enjoy. :guitar:

---

