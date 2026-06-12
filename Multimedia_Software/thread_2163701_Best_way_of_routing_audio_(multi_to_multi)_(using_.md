---
title: "Best way of routing audio (multi to multi) (using pulse audio)"
date: 2013-07-19
forum: Multimedia Software
---

### Post by Cynar on 2013-07-19
I'm working on an audio project for my local hackspace and before I get in too deep, I'm hoping you guys might be help me out.

First, does anyone know of any existing project and/or examples I can use as a base/learning aid?

Am I going about this the right way?

How deep a hole am I digging? (I'm still fairly new to linux, at least when properly under the hood)


I'm trying to do multi-room audio from a single central computer. The system needs to be easy to reroute, and run with only a web interface.
As it stands, I am using MPD as a player with multiple instances running, with a PHP control page each.
The Computer has 4 sound cards, but I need 5 outputs. 1 of the cards has multiple outputs though.

I am currently planning on using Pulse Audio to route from the players to the cards in a dynamic way.

[TABLE]
[TR]
[TH]Real Sources        [/TH]
[TH]     -->    [/TH]
[TH]Virtual Sink/Sources    [/TH]
[TH]-->    [/TH]
[TH]Virtual Sink    [/TH]
[TH]-->    [/TH]
[TH]Sound output[/TH]
[/TR]
[TR]
[TD]MPD Global (1)        [/TD]
[TD]-->    [/TD]
[TD]Source 1        [/TD]
[TD]XXX    [/TD]
[TD]Sink 1        [/TD]
[TD]-->    [/TD]
[TD]Sound Card 1 (L & R)[/TD]
[/TR]
[TR]
[TD]MPD R&R (2)        [/TD]
[TD]-->    [/TD]
[TD]Source 2        [/TD]
[TD]XXX    [/TD]
[TD]Sink 2        [/TD]
[TD]-->    [/TD]
[TD]Sound Card 2 (L & R)[/TD]
[/TR]
[TR]
[TD]MPD Teaching (3)    [/TD]
[TD]-->    [/TD]
[TD]Source 3        [/TD]
[TD]XXX    [/TD]
[TD]Sink 3        [/TD]
[TD]-->    [/TD]
[TD]Sound Card 3 (L & R)[/TD]
[/TR]
[TR]
[TD]MPD CNC (4)        [/TD]
[TD]-->    [/TD]
[TD]Source 4        [/TD]
[TD]XXX    [/TD]
[TD]Sink 4        [/TD]
[TD]-->    [/TD]
[TD]Sound Card 4 (FL & FR)[/TD]
[/TR]
[TR]
[TD]MPD Workshop (5)    [/TD]
[TD]-->    [/TD]
[TD]Source 5        [/TD]
[TD]XXX    [/TD]
[TD]Sink 5        [/TD]
[TD]-->    [/TD]
[TD]Sound Card 4 (BL & BR)[/TD]
[/TR]
[TR]
[TD]MPD WetRoom (6)    [/TD]
[TD]-->    [/TD]
[TD]Source 6        [/TD]
[TD]XXX [/TD]
[/TR]
[TR]
[TD]MPD Announce (7)    [/TD]
[TD]-->    [/TD]
[TD]Source 7        [/TD]
[TD]XXX 
[/TD]
[/TR]
[/TABLE]
[TABLE="width: 800"]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[/TABLE]
 
The Mixing layer (XXX) will be controlled by the Routing page (via PHP and scripts?) 
The default workmode is to route Global (1) to all 5 outputs. 
Announce (7) is able to override and play to all channels, without permanently changing the base routing.

Is this something that pulseaudio can be cofigured to do in a reasonable way? If so, what is the best way of controlling the re-routing? 

The base computer is running the newest version of Xubuntu.

---

