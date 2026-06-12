---
title: "using my laptop as a media center controller"
date: 2010-02-11
forum: Multimedia Software
---

### Post by odsus1 on 2010-02-11
Hey guys, ok this is a two part question:
i am using ubuntu media on a desktop for all of my multimedia needs and i just installed jaunty (alt install) on an old gateway solo laptop(266 mhz and 186mb ram) to use as my controller/remote using desktop sharing, the problem is the laptop can't keep up with the desktop and everything is all jerky (especially watching dvds). So here are the questions, what can i uninstall from the laptop to make performance better and/or is there another option short of buying a wireless keyboard/mouse (I'm poor and use what I have(besides i like having an up-close display for text and stuff)). Also I don't care about, doing anything else with this laptop, internet file-browsing audio; anything, all i want is the remote desktop viewer; thanks:
Odie

---

### Post by Maheriano on 2010-02-11
Faster processor, more RAM, faster RAM, better wireless card.
Basically you need a new laptop.

---

### Post by odsus1 on 2010-02-11
That's what i though, but a boy can dream, can't he?

---

### Post by Maheriano on 2010-02-11
I got a Dell Studio 15 with a T6400 dual core processor wirelessly connected to my desktop via NXClient and I tried streaming a video once. It was really choppy even on that machine simply because I was running on G wireless speeds. So you got a long ways to go.

---

### Post by odsus1 on 2010-02-11
Like I said, all i want is a controller, I don't want to watch video on my laptop. i just want to be more than 4 feet away from my screen when navigating, i.e. sitting on my couch...

---

### Post by jamesdew on 2010-02-12
you could install XBMC on your main machine and then control the main machine through the XBMC web ui.

Maybe other media players have network control interfaces im not sure. But XBMC is the best way to watch media imo anyway.

---

### Post by Maheriano on 2010-02-12
> **odsus1 said:**
> Like I said, all i want is a controller, I don't want to watch video on my laptop. i just want to be more than 4 feet away from my screen when navigating, i.e. sitting on my couch...
You just want a controller? You said you were trying to stream video. Okay well that's easy, there are multiple options for this:

1. Set up NXClient on your machines and you can get a visual session representation of your machine on your laptop. This will let you change the music your desktop is playing by hitting the buttons on your laptop as if you were at your desktop. This is what I do.

2. Set up SSH on your phone with macros to send commands to your desktop to change the music or play movies or whatever. Command line and confusing.

3. Set up something like Tesla Remote Control (search for it on these forums) on a PDA like a HTC and control media that way. This is where I'm heading with mine.

4. Set up voice recognition with microphones spread throughout the area and control it by talking.

---

### Post by odsus1 on 2010-02-14
Wow, I had never heard of xbmc(I've never owned an x-box either) that sounds like the deal, I am downloading the live cd as we right now, is the web ui difficult to set up?

---

### Post by odsus1 on 2010-02-14
> **Maheriano said:**
> You just want a controller? You said you were trying to stream video. 

Remote desktop displays what is on the other desktop, so in essence I was streaming.

So what you are saying is that I can control my media player with my blackberry? That's cool too. Now when you say command line and confusing, I can handle command line; as long as someone is telling me what to type: i can handle confusing; as long as someone is telling me what to type. I know enough to install packages and such, but beyond that I am pretty much an idiot what it comes to the command line.

---

### Post by jamesdew on 2010-02-16
> **odsus1 said:**
> Wow, I had never heard of xbmc(I've never owned an x-box either) that sounds like the deal, I am downloading the live cd as we right now, is the web ui difficult to set up?

nope just as simple as ticking a box

---

### Post by Maheriano on 2010-02-17
> **odsus1 said:**
> Remote desktop displays what is on the other desktop, so in essence I was streaming.

So what you are saying is that I can control my media player with my blackberry? That's cool too. Now when you say command line and confusing, I can handle command line; as long as someone is telling me what to type: i can handle confusing; as long as someone is telling me what to type. I know enough to install packages and such, but beyond that I am pretty much an idiot what it comes to the command line.

Basically you send command line arguments to the application. Like I have all the lighting in my house hooked up to my computer via X10 and controlled via a command line program called Heyu. If I want to turn on my basement light, I type ```
heyu on c1
```
So I could use midpSSH on my Blackberry, SSH into my home machine and send the command line from my Blackberry to turn on that same light. You'd go the same route with command lines to your media application.

---

