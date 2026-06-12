---
title: "HOWTO: Streaming audio between TWO Ubuntu computers"
date: 2010-12-11
forum: Multimedia Software
---

### Post by NertSkull on 2010-12-11
So I spent 3 days trying to figure this out and finally got it to work.  I couldn't find a lot on what I wanted, so I put something together for me to remember how to do it in the future, and I figured others may find it useful.

[SIZE="5"]How to stream music between two computers.[/SIZE]

[SIZE="4"]Background[/SIZE]

There are lots of tutorials and information on how to set up a multicast system to stream audio.  Where one source computer plays the music, and 3+ receiving computers pick up the audio.  But multicasting uses UDP so it wasn't very reliable for me.

Besides I only have two computers, so I don't need support for more than just the two.  All I needed was the ability to listen to music downstairs and upstairs.  So I looked into streaming directly.

[SIZE="4"]What this is for[/SIZE]

Streaming audio between TWO computers.  If you want more than that, you need to look up pulseaudio multicasting abilities.

Multicasting is MUCH easier to set up.  But I found the quality was worse.  It may be perfect for your needs.

[SIZE="4"]Basic theory of what you are doing[/SIZE]

You need to set up pulseaudio to transmit and receive sound on both the **source** computer and the **receiving** computer.

In this guide I set up transmission and receiving on both computers.  So each could stream to eachother.  It should be pretty self explanatory on what you would need to change to make a unidirectional system.  But for this, we'll do both

[SIZE="4"]How to do it - Part I[/SIZE]

I wrote this from a very basic perspective.  But I need simple.

[SIZE="3"]1. Check that you have the following items installed on both **source** and **receiver** computers[/SIZE]
[INDENT]paprefs (pulseaudio preferences)
pavucontrol (pulseaudio volume control)
padevchooser (pulseaudio device chooser) - not required
pulseaudio-utils (this was installed on mine already, but somewhere mentioned it was needed, so might as well make sure)

```
sudo apt-get install paprefs pavucontrol padevchooser pulseaudio-utils
```

[/INDENT][SIZE="3"]2. Open up the pulse audio preferences on computers on **BOTH** computers.[/SIZE]

[INDENT]You can find it in System>Preferences.  Or,

```
paprefs &
``` In a terminal[/INDENT]

[SIZE="3"]3. Find the tab Network Access and check "make discoverable..." on **BOTH** computers.[/SIZE]

[SIZE="3"]4. Find the tab Network Server and check "enable network access...." on **BOTH** computers.[/SIZE]

[INDENT]4a. Also check "allow other machines..." and "don't require authentication" on **BOTH** computers.

[COLOR="navy"]SEE NOTE 1 AND 2[/COLOR][/INDENT]

[SIZE="3"]5. Now go to your source computer (where you play your music) and start playing something.[/SIZE]

[INDENT]Open Rythmbox, VLC, Guayadeque or something similar and play some music[/INDENT]

[SIZE="3"]6. Open pulseaudio volume control[/SIZE]

[INDENT]Applications > Sound&Video > Pulse Audio Volume Control  OR

```
pavucontrol &
```[/INDENT]

[SIZE="3"]7. Find the playback tab[/SIZE]

[INDENT]7a. Your audio program (rythmbox, guayadeque, VLC, etc) should be listed.

[COLOR="Blue"][COLOR="Navy"]SEE NOTE 3[/COLOR][/COLOR]

7b. On the same line as your music player there will be a button/pull down that lets you select another "sink".  Choose the one on the other computer.  Normally it will say "something@pc-name" to help you choose.

[COLOR="navy"]SEE NOTE 5 AND 6 if you don't have the right options[/COLOR]
[/INDENT]
[SIZE="3"]8. Once selected, music should start to play on the receiving computer.[/SIZE]



BUT...Its not playing on the source computer anymore.  The next steps fixed that for me.

[SIZE="5"]PART II[/SIZE]

**_All Steps in Part II are done on the SOURCE computer (except step 11a)_**

[SIZE="3"]9. Stop the music from playing (if it is).[/SIZE]

[SIZE="3"]10. We have to configure some modules with pulse audio and combine two sinks (audio cards) so that it will play on the source and receiver at the same time.[/SIZE]

[SIZE="3"]11. First you need information.[/SIZE]

[INDENT]11a. The IP of the receiving computer (i.e. 192.168.0.12).  I suggest making a static IP on the receiver.  On the receiving computer you can run the following in the terminal and find your IP.

```
ifconfig
```

[INDENT]Also I believe there is a way to not use the IP and use something like "server.local" but I haven't gotten that to work.[/INDENT]

11b. You also need the name of the sound card ("sink") on the source machine.  

[INDENT]You will combine the name of the source machine sound card with the IP of the receiving computer.  This works because the receiving computer is broadcasting its audio information.

[INDENT]11b-1. Open a terminal and type 

[INDENT]```
pacmd list-sinks
```

pacmd is the pulse audio command line call[/INDENT]

11b-2. Find the name of the card on the source machine you want to play.

[INDENT]You will have to do some detective work here and find your name.  For me it was the first one in the list.  You want the name of the local card.  Do not use the cards from the receiver, use the source card.

You'll see a bunch of things name, driver, flags, etc.  You want to copy the "name" down without the brackets.  We will use that to combine sinks.

Mine was something like "alsa_output.pci-0000_00_7.2.analog-stereo"[/INDENT][/INDENT][/INDENT][/INDENT]

[SIZE="3"]12. Now we load the tunnel sink on the source computer[/SIZE]

[INDENT]The combine command below only works on local sinks.  So first we pull in the receiving computer's information so we can use it.
```
pacmd load-module module-tunnel-sink server=soundserver.local
```

You need to replace soundserver.local with your value (i.e. mine looked like "server=192.168.0.12" for me)[/INDENT]

[SIZE="3"]13. Now we combine the sinks on the source computer.[/SIZE]

[INDENT]```
pacmd load-module module-combine sink_name=combined slaves="tunnel.soundserver.local,name_of_your_card"

```

So mine looks like

```
pacmd load-module module-combine sink_name=combined slaves="tunnel.192.168.0.12,alsa_output.pci-0000_00_7.2.analog-stereo"
```
[/INDENT]

[SIZE="3"]14. Now we should be ready, go to the source computer and turn on some music again.
[/SIZE]
[SIZE="3"]15. Go to the playback tab on the pulseaudio volume control. (Just like before)
[/SIZE]
[SIZE="3"]16. Find your audio player and go the the drop down list.  
[/SIZE]
[INDENT]You should (if things worked) see a combined sink that says something like simultaneous output on.....  When you choose it, it will now play on both computers.

Or you can choose to just play on one computer or the other.

Notice also this is application dependent.  So you can have zero, one or more applications playing to the other computer or both computers.

Also it should save your settings in the playback tab.  So as long as the server is on, it should play on both.  But I've discovered that doesn't always stay the case with me if I turn the server off.  I will often have to repeat the module loading steps, but its at unpredictable times.  I don't know how to fix that yet.

[COLOR="Navy"]SEE NOTE 7[/COLOR]
[/INDENT]
[SIZE="4"]Notes[/SIZE]

1. From step 5 on you should have the server discovery on for the remaining steps(what we did in 1-4).  You can turn it off later when you have things set up but aren't playing music on both computers.  
[INDENT]1a. [COLOR="DarkRed"]I do turn mine off.  Because even when music isn't being played it is still streaming over your network and eating your bandwidth[/COLOR].

To turn off the stream, I just go to one computer (you could go to both) and open the pulse audio preferences.  Then I uncheck everything in the "Network Access" and "Network Server" tabs.  Then at least one computer isn't listening, so nothing gets transfered[/INDENT]

2. Steps 1-4 is where you would set up a unidirectional system if you wanted that.

4.I haven't tested this, but I'm told some music players don't use pulse normally.  I've heard mythtv and amarok have issues, but I have not confirmed these or any others other than I know I've gotten it to work with my Guayadeque.

[COLOR="DarkRed"][B]5. I had to have my firewall turned off on both computers to get things recognized.  Once I can figure out what ports need opening I'll post.  But for now I had to turn it off.  If anyone knows the ports let me know.  UPDATE** I believe you need port 4713 open.  I need to look into this more.  But if I have port 4713 open it seems to work with the rest of the firewall on.  I'll try to confirm this.
[/B][/COLOR]

6. If you did have a firewall on.  Or if you don't see something.  You may need to turn on and off the server stuff in steps 1-4 a few times.  I found if I did it too quick sometimes things didn't load.  Once or twice I even had to reboot inbetween.  It seems to be a little picky, but it should work.

7.  I don't know why, but sometimes I find the fact that it saves my settings to actually be a problem.  About 60% of the time, if I start playing my music player with it remembering the previous setting, it gets scratchy.  So I have to stop it, set it to only play on the source computer.  Then turn it back to playing simultaneously on both.  And like I said sometimes it appears to not even save.  Its not a perfect solution yet.

7a. Similarly, I find (again this may just be my setup and network) but it takes about 1-2 minutes for it to clear up in sound.  

8.  I can't say I found this to be the most ideal solution in the world.  It works pretty well.  But sometimes it is scratchy or not the best sound quality.  Also I've found that on WiFi it will sometimes get out of sync between the computers (which I only notice if I'm in a room halfway between the two computers).  But all things considered it works pretty decent.

9.  From my understanding, KDE uses something other than pulseaudio.  So this won't work.  I'm not 100% sure on that, but from what I've read thats what I understand.



[SIZE="4"]House-Keeping[/SIZE]

Here are some useful tricks that I use when I need to change things

To list the modules installed (including the ones we just installed) use this
```
pacmd list-modules
```

Then you can delete/unload modules if you did something wrong.  Just find the index number from the command above and use the following.
```
pacmd unload-module ##
```

You can open the pulse audio device chooser (which we installed) for more options.  It opens as a tray/panel icon

[SIZE="4"]Notes on what I used[/SIZE]

I was using my motherboards analog onboard audio cards for BOTH computers.  Eventually I want to try this with other settings (like HDMI or an optical out) but thats for another day.

On the source computer I was running Ubuntu 10.10 and on the receiving computer I was running Ubuntu 10.04.

I have zero idea if this will work on any other configuration (although I can't see why it wouldn't).

Personal Note:  This is the first time I've ever attempted to put a tutorial/howto together and posted it.  So I apologize if its a little rough or confusing.  Let me know and I'll try to clarify where needed.

---

### Post by nothingspecial on 2010-12-11
Wow, you did a lot of work here.

I admire it :D

[SIZE=1]There are a few easier ways of doing this, but I`m not going to sit here telling you what you should have done.[/SIZE]

I think this is a very very well written turorial tutorial :D, with plenty of explanation about what is going on.

Cheers & thanks.

---

### Post by spektre1 on 2011-01-19
Thank you so much for this, it shines light on an obscure problem.

I hunted for an hour earlier to find out exactly how to do this, and only just now found this after walking away from the problem. Going to try it again when I get into work in the morning.
It's a client/server model problem, and the sink/source terminology doesn't make a ton of sense unless you're thinking of it that way. You have to control where the source goes, from the source... so it's kind of like pointing the hose. Which is just kind of weird.

Will report results, and probably test thoroughly. And play with the multicasting, this is something I'm doing for a living now, so I want to know more about it.

---

### Post by cacasodo on 2011-02-23
Dude! 
Awesome post!  Thanks man..with a bit of finagling, it worked like a charm.
thanks!
'sodo

---

### Post by Sonja on 2011-05-07
Is there a command-line way to do it, if I only have terminal access to one of the two computers?

```

room@room:~$ paprefs &
[1] 8034
room@room:~$ 
(paprefs:8034): Gtk-WARNING **: cannot open display: 

```

---

### Post by nothingspecial on 2011-05-07
On the computer with the music

```
vlc -vvv -I dummy [COLOR="Red"]song.mp3[/COLOR] --sout '#standard{access=http,mux=ogg,dst=[COLOR="Red"]192.168.1.10[/COLOR]:8080}'
```

Change the music and ipaddress accordingly.

Then in another shell on that computer and in a terminal on the other computer

```
mplayer http://192.168.1.10:8080
```


Music in sync :guitar:

---

