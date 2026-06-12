---
title: "open pro tools?"
date: 2006-03-21
forum: Multimedia &amp; Video
---

### Post by boblatorm on 2006-03-21
if someone reverse engineered pro tools for linux, i'd pay good money :D


that is all.

---

### Post by dolson on 2006-03-21
Well, the closest thing to that is Ardour. And they would love your money.

---

### Post by MetalMusicAddict on 2006-03-21
[QUOTE=dolson]Well, the closest thing to that is Ardour. And they would love your money.[/QUOTE]
I second that. :)

---

### Post by boblatorm on 2006-03-21
E: Couldn't find package ardour


ive just got that every times ive tried to install...  :(

edit: whoops, ardour-gtk it is :p

---

### Post by dolson on 2006-03-21
That's not the package name..

Either use Synaptic's search feature, apt-cache search, or enable tab-completion in /etc/bash.bashrc so that you can tab-complete software to install... for instance, sudo apt-get install ardour<TAB> would list all the matches.

The package you want is likely ardour-gtk or ardour-gtk-i686 or whatever it is.

Tab-completion is VERY handy, beyond apt-get... I highly recommend it, and am puzzled as to why it ships disabled.

---

### Post by Joey French on 2006-03-21
How do you enable it then? I am not at my box, so I can't search for it, but go ahead and tell us. It sounds useful.

---

### Post by dolson on 2006-03-21
Edit the file /etc/bash.bashrc that I mentioned. You'll see it in there, it's an IF block of about 3 lines that is commented out. Just uncomment them.

---

### Post by klahjn on 2006-03-21
Installing ardour now, it seems like a very useful program.

---

### Post by cleentrax on 2006-04-02
Well, ProTools is primarily useful because of its proprietary hardware, which costs tens of thousands of dollars. I would be much happier to see an open SONAR, which is the current leading software-based digital audio workstation. 

Ardour is an audio recorder/mixer, which is just one small slice of what SONAR does. Rosegarden, though meager, is the only combo midi/audio workstation for Linux that I know of, but it is a KDE app and I'm a Gnome kind of guy...

---

### Post by dolson on 2006-04-04
[QUOTE=cleentrax]Well, ProTools is primarily useful because of its proprietary hardware, which costs tens of thousands of dollars. I would be much happier to see an open SONAR, which is the current leading software-based digital audio workstation. 

Ardour is an audio recorder/mixer, which is just one small slice of what SONAR does. Rosegarden, though meager, is the only combo midi/audio workstation for Linux that I know of, but it is a KDE app and I'm a Gnome kind of guy...[/QUOTE]

I guess that your choice is simple, then.

Rosegarden & KDE libs under GNOME
or
SONAR & Windows.

The third option is to do something about it, either by becoming a developer or fronting the cash to fund development on a GNOME-based application of what you seek. Either of these solutions is fine by me. But if I were putting up the cash, it would definitely go to Ardour, if they are willing to do what you want.

And by the way, in the Linux world, traditionally there is one app per task, and it does it well. SONAR is from the Windows world, where apps more often than not do not interoperate freely, and competition is for dollars. In my world, interoperability is key, and JACK is that central hub that connects your sequencers to your synths to your drum machine to your audio recorder to your mastering software.

---

### Post by cleentrax on 2006-04-04
[QUOTE=dolson]I guess that your choice is simple, then.

Rosegarden & KDE libs under GNOME or SONAR & Windows.
[/QUOTE]

Well that's an easy choice. SONAR. 

> And by the way, in the Linux world, traditionally there is one app per task, and it does it well

I don't have a philosophical issue with that approach. But I haven't had any success getting JACK running, so I can't actually test it out. Let me ask some questions:

1. Can I route softsynths/samplers (say, QSampler) to an audio track (say, in Ardour) in real time in order to add audio plugin effects and automation during performance/recording?
2. Can I use one interface to control all tempo, key and transport changes across multiple apps, or do they have to be made in each app separately?
3. Can I  mix down a project that includes MIDI-triggered samples and synths, without having to first record them to a linear audio track?
4. Can I take automation on a  MIDI track (say, from Muse or Rosegarden) and apply it to an audio track (say, in Ardor)?

---

### Post by dolson on 2006-04-04
Heh, I don't like KDE either. I don't use Rosegarden anymore either, but instead Seq24. It may not be what you want though. I am also a GNOME kinda guy. But there are many Qt apps that are not mirrored in the GTK world (yet.. hopefully..), so it's a small sacrifice, IMO, to suck it up and suffer with Qt/KDE libs. In an ideal world, this would be a non-issue, as both desktops would have a full suite of apps, but that isn't the case right now, unfortunately.

On to the rest of your post.

Clearly you are more of a "pro" than I am, because I only started looking at software-based music production earlier this year, and cannot answer all of your questions. I hope someone here can, but I surely cannot. However, I can try and answer some of them.

1. Yes, you can route anything into anything with JACK. I do not know if adding a plugin in Ardour will apply to the softsynth in realtime; I assume so. If not, I know that a lot of people seem to use JACK-Rack, but I don't see the need. I have used Ardour very limitedly, but it is very flexible, and I would be surprised if I am wrong about this.

2. Any app that works with the JACK Transport should be able to handle all of this, with the exception of maybe key changes.. That would likely be up to your sequencer software, but I'm not 100% sure.

3. I'm not sure if I'm using terms the same as you, but if you want to perform your song in real-time, and stream it to disk, then yes, you can do this. I would have to read up about how to do it with Ardour, because I have only used it for one project so far, and am not intimately familiar. But I know that you can route anything that goes to your speakers into TimeMachine and record it that way, and then you'd more than likely want to master it with JAMin. If you want to master in realtime, without mixing down to a single stereo track first, I say good luck! I'm sure if you have a very powerful system, or use very high latency (which is not critical at this stage) then you could do it, but it doesn't make a lot of sense.

4. This one for sure I have no idea about. Sorry man.

---

### Post by cleentrax on 2006-04-04
Thanks for the responses. I'm looking forward to testing JACK connections between apps.

As for #4, I don't want to do it in real-time -- I can do that with a reel to reel! Many of my projects are for feature films -- I have the processing power to mix them down offline in less than a minute, but it might take an hour to do a realtime mix.

---

### Post by peanut butter on 2006-04-17
whats the problem with kde? its just the libs.

---

### Post by dolson on 2006-04-17
No, it is not "just" the libraries. It's the entire look and feel, and when you launch Rosegarden, it launches a bunch of extra garbage in the background.

---

