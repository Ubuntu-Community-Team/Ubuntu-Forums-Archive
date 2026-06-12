---
title: "Exaile doesn't have plugin. But VLC works."
date: 2009-12-30
forum: Multimedia Software
---

### Post by Roasted on 2009-12-30
I just set up Kubuntu on my work laptop and was trying to play an audio CD. My music player of choice is Exaile, and Exaile hits me with an error I've never had in all of my years of using *buntu with Exaile:

You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

But the same audio file plays in VLC. Hmmmm? What am I missing? I have w64 codecs, medibuntu, and restricted extras. *shrug*

---

### Post by Uncle Spellbinder on 2009-12-30
I'm on Windows at the moment, so I can't check. But check the plugins in Exaile itself. Under preferences. There might be a CD plugin not checked. Just a guess.

---

### Post by Roasted on 2009-12-30
I pulled the mp3 off of the CD and tried to run it locally too. No dice.

---

### Post by Yellow Pasque on 2009-12-30
Exaile uses gstreamer and the gstreamer packages usually aren't installed by default on kubuntu. Just make sure you don't install pulseaudio if you don't have it installed already. INstall gstreamer0.10-alsa first to minimize your chance of that.

---

### Post by Roasted on 2009-12-30
Good tip - but it worked out of box with my Kubuntu install on my desktop. Only difference is that's 9.04 cause 9.10 hated my desktop, while I'm on 9.10 on my laptop where I'm running into this issue.

It's no biggie cause I'm finding I actually like Amarok 2, but even still it confuses me.

---

### Post by Yellow Pasque on 2009-12-30
Ok, so what does exaile say when you run it in a terminal?

---

### Post by WeAreTheSiNs on 2010-01-22
> **Temüjin said:**
> Ok, so what does exaile say when you run it in a terminal?

Im having this same problem..
heres what it says in terminal:

> INFO    : Loading Exaile 0.3.0.1...
INFO    : Loading settings...      
INFO    : Setting up deferred idle manager function...
INFO    : Loading plugins...                          
INFO    : Loading collection...                       
INFO    : Loading devices...                          
INFO    : Loading interface...                        
INFO    : HAL Providers: [<cd.CDHandler object at 0x8fa76cc>]
INFO    : Loading main window...                             
INFO    : Loading panels...                                  
INFO    : Connecting panel events...                         
INFO    : Connecting main window events...                   
INFO    : Done loading main window...
INFO    : Playing file:///media/Old%20computer/Program%20Files/Jeremys%20%20iTunes%201/itunes%20Music/Cradle%20Of%20Filth/Damnation%20and%20a%20Day/05%20Damned%20In%20Any%20Language.mp3
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
ERROR   : <gst.Message GstMessageError, gerror=(GstGError)NULL, debug=(string)"gstplaybasebin.c\(2327\):\ prepare_output\ \(\):\ /GstPlayBin:player"; from player at 0x9416040> ['__class__', '__cmp__', '__delattr__', '__dict__', '__doc__', '__format__', '__getattribute__', '__grefcount__', '__gstminiobject_init__', '__gtype__', '__hash__', '__init__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'copy', 'flags', 'parse_async_start', 'parse_buffering', 'parse_buffering_stats', 'parse_clock_lost', 'parse_clock_provide', 'parse_duration', 'parse_error', 'parse_info', 'parse_new_clock', 'parse_request_state', 'parse_segment_done', 'parse_segment_start', 'parse_state_changed', 'parse_step_done', 'parse_step_start', 'parse_stream_status', 'parse_structure_change', 'parse_tag', 'parse_tag_full', 'parse_warning', 'set_buffering_stats', 'set_seqnum', 'src', 'structure', 'timestamp', 'type

---

### Post by Roasted on 2010-01-22
I'm not convinced this is a Kubuntu problem.

Why?

Just installed Ubuntu.

I have medibuntu.

...Same issue with Exaile.

---

### Post by WeAreTheSiNs on 2010-01-22
To fix this problem: sudo apt-get install ubuntu-restricted-extras

 yes i meant Ubuntu not kubuntu

---

