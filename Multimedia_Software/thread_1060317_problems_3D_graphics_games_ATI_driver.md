---
title: "problems 3D graphics games ATI driver"
date: 2009-02-04
forum: Multimedia Software
---

### Post by nemo.r on 2009-02-04
I'm running Ubuntu 8.10 on a Toshiba Satellite L300D laptop, with the ATI Radeon HD 3100 graphics card.

Video playback all works fine, streaming from the Internet and DVD and downloaded clips.

However I cannot play any games.

I installed Fable (in wine) and tried to play, the screen went black as the game loaded then I got a white screen then lots of small multi coloured horizontal bars. When I move the mouse a kind of haze of multi coloured bars move around, and when I press exit the colours change, so clearly the keyboard and mouse are having some affect. Just the graphics are screwed.

I assumed my laptop didn't have the right specs to play Fable and I installed Savage2, however I've now had exactly the same problem, (only now the predominant colour is red, not white, but I guess that's because the intro screen in Savage2 is red.)

I removed the fglrx drivers and tried the game and this time I could see the background, but any foreground objects where white, (white silhouettes) and the buttons in the centre where white.

If I try to get a screen shot it just shows up as a black screen. I will try to get a photo scanned, but basically the screen is divided into lots of columns about an inch wide, made up of small 2/3 pixel height horizontal coloured bars).

I've now installed Jack Keane in wine and I'm getting it again, audio fine, screen predominately white with blue lines on the screen.

Any help appreciated.

---

### Post by nemo.r on 2009-02-05
I downloaded and installed the driver from ATI, (catalyst 9.1) it seems to have solved the problem with the games, however everything is very slow now. The splash screen an intro as I power up my laptop. as well as the intro as I start Jack Keane, (the strategy first splash screen etc. and the 'loading' before the main menu) Both take ages to load.

When I watch videos that have been downloaded, (e.g. quicktime trailers) the screen refreshes slowly, like a ripple every half a second that goes down the screen. (Streamed videos are fine however) The same happens when scrolling down web pages or scrolling down a word document.

Also general graphics are slow, opening documents load slowly etc.

I don't have compiz on, but this isn't like the flickering I encountered before when I had compiz, this is just the graphics refreshing too slowly.

---

### Post by nemo.r on 2009-02-09
Well I fixed it using the instructions in this wiki

[http://wiki.cchtml.com/index.php/Troubleshooting#Graphical_Anomalies]("http://wiki.cchtml.com/index.php/Troubleshooting#Graphical_Anomalies")

Powering up is still rather slow as is the loading startup for the games, but they're mostly working, the odd bugs are I think unrelated to the ATI driver, and just to do with running windows games in wine.

Rather a useless thread I do apologise, but perhaps it'll help some other noob.

I can't see how to mark this thread as solved so if someone could show me then I'll do so.

---

