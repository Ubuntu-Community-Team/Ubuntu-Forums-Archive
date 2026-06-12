---
title: "JACKing Seq24"
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by redsp1der on 2006-10-02
Hi

I've just started going through the Ubuntu Studio tutorials and so far everything has gone pretty well. My orginal Audigy sound card seems to be working and my MIDI keyboard is working too. Using JACK I've been able to link the keyboard to ZynAddSubFX or Hydrogen and make some sounds.

My problem is with seq24. In the Seq24 tutorial one of the first steps is to wire up Seq24 but Seq24 doesn't show up in the available connections.
What am I doing wrong?

BTW, I am very new to linux. I decided to install Xubuntu onto my old P3 866mhz on a whim.

---

### Post by dolson on 2006-10-02
To me, it sounds like you aren't launching seq24 the way it says to in the tutorial, but rather clicking on the icon or something.

---

### Post by kellogs on 2006-10-02
look in seq24 options, the only default options you will need working are "jack transport" and "transport master" these in ON mode for seq24 to start and end as master(if you need to save sequences in ardour for example).

If you look now at jack connections, Seq24 is invisible, but connected(in my case its (62:midi-through->0-midi-through-port0) in the MIDI tab. But it is not visible in the Audio Tabs.

If you dont see it in the midi tab check the ubuntu studio wiki and check for a problem with Alsa-midi.

---

### Post by dolson on 2006-10-02
Setting the transport mode doesn't change how seq24 routes the MIDI.. **seq24 --manual_alsa_ports** is what he is after.

---

### Post by redsp1der on 2006-10-02
yeah that was my problem. I was just clicking on the icon. thanks

Is there anyway to set up seq24 so I can just click on the icon rather than remember another command?

Making music with Linux seems to have potental but I'm finding Linux in general to be somewhat frustrating. I find myself just throwing random lines of code into the terminal because someone on the internet says to do it.

---

### Post by dolson on 2006-10-03
The reason I put everything by commands is that it's easier than putting screenshots and detailed GUI instructions when a single command suffices. It's a tradeoff that I decided on, so that I could focus on content rather than prettiness. But I understand totally where you are coming from.

That said, to answer your question, on Edgy, it appears that either manual_alsa_ports is the default for seq24, or it remembers your choice. Either way, on Dapper you *should* be able to do this:

Edit your ~/.seq24rc file and find the section here:

> [manual-alsa-ports]
# set to 1 if you want seq24 to create its own alsa ports and
# not connect to other clients
1

If it's a 0, set it to a 1.

I can't test it, but it should be possible on Dapper. Otherwise, Edgy is coming soon... :)

---

