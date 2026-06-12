---
title: "Rhythmbox in the Terminal?"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by derouge on 2007-03-20
Is there anyway to display what song Rhythmbox is playing in the terminal? What I ultimately want to do is somehow grab this information and have it displayed, using Conky, on my desktop. From my very limited understanding, Conky has built-in commands that support MPD and Audacious music player backends. But Rhythmbox doesn't use either of these, correct? Excuse me if my terminology is off .. this is new territory for me.

So in short: I'd like to be able to run a shell script that tells me what song Rhythmbox is currently playing. Doable?

---

### Post by GSF1200S on 2007-04-10
> **derouge said:**
> Is there anyway to display what song Rhythmbox is playing in the terminal? What I ultimately want to do is somehow grab this information and have it displayed, using Conky, on my desktop. From my very limited understanding, Conky has built-in commands that support MPD and Audacious music player backends. But Rhythmbox doesn't use either of these, correct? Excuse me if my terminology is off .. this is new territory for me.

So in short: I'd like to be able to run a shell script that tells me what song Rhythmbox is currently playing. Doable?

Amen! Ive been trying to figure this one out for awhile.. Its too bad someone hasnt responded with an answer. 

If someone reads this and knows its impossible, let us know... I would really like to have this feature.

---

### Post by reclusivemonkey on 2007-04-10
It should be possible with python; there's a python console right in rhythmbox.

---

### Post by GSF1200S on 2007-04-10
> **reclusivemonkey said:**
> It should be possible with python; there's a python console right in rhythmbox.

Wow, always something new to learn.. 

I enabled the python console in rythmbox, but when I clicked on it, it came up with:

You can access the main window through the 'shell' variable :
<rb.Shell object (RBShell) at 0x8700cfc>
>>>

From here, im lost. I just got into doing scripts yesterday while tinkering with Conky, so im a noob once again..

Any ideas?

---

### Post by reclusivemonkey on 2007-04-10
> **GSF1200S said:**
> Wow, always something new to learn.. 

I enabled the python console in rythmbox, but when I clicked on it, it came up with:

You can access the main window through the 'shell' variable :
<rb.Shell object (RBShell) at 0x8700cfc>
>>>

From here, im lost. I just got into doing scripts yesterday while tinkering with Conky, so im a noob once again..

Any ideas?

Nope, sorry I know less about Python than I do about shell scripting. There are some existing python plugins that get the track listings, so I would have a look at those for a start. There might also be an irc channel for Rhythmbox which may have some knowledge you can tap.

---

### Post by GSF1200S on 2007-04-10
> **reclusivemonkey said:**
> Nope, sorry I know less about Python than I do about shell scripting. There are some existing python plugins that get the track listings, so I would have a look at those for a start. There might also be an irc channel for Rhythmbox which may have some knowledge you can tap.

Cool, thanks alot...:)

---

### Post by doclivingston on 2007-04-11
> **derouge said:**
> So in short: I'd like to be able to run a shell script that tells me what song Rhythmbox is currently playing. Doable?

rhythmbox-client --print-playing


> **reclusivemonkey said:**
> There might also be an irc channel for Rhythmbox which may have some knowledge you can tap.

For reference it's #rhythmbox on irc.gimp.net

---

### Post by reclusivemonkey on 2007-04-11
> **doclivingston said:**
> rhythmbox-client --print-playing

Fantastic! Thanks for that =]

---

### Post by GSF1200S on 2007-04-11
> **doclivingston said:**
> rhythmbox-client --print-playing




For reference it's #rhythmbox on irc.gimp.net


No doubt this works like a champ in the terminal, but it doesnt work in Conkyrc.. this is the relevant input in Conkyrc:

${color lightgrey}Now Playing: ${color} ${rhythmbox-client --print-playing}

But when I do that, conky pops up with:

Now Playing: ${rhythmbox-client}

Any ideas?

---

### Post by reclusivemonkey on 2007-04-11
> **GSF1200S said:**
> 
${color lightgrey}Now Playing: ${color} ${rhythmbox-client --print-playing}


Should be

```

${color lightgrey}Now Playing: ${color} ${exec rhythmbox-client --print-playing}

```

---

### Post by GSF1200S on 2007-04-12
> **reclusivemonkey said:**
> Should be

```

${color lightgrey}Now Playing: ${color} ${exec rhythmbox-client --print-playing}

```

Ha! Well, it displays a song when a song is playing, but I have a very undesirable result. On bootup, it automatically launches rythmbox.. and to make it worse, if I try to close rythmmbox it automatically opens it back up! Any ideas on how to fix this? (The text shows on conky just fine though...)

---

### Post by reclusivemonkey on 2007-04-12
> **GSF1200S said:**
> Ha! Well, it displays a song when a song is playing, but I have a very undesirable result. On bootup, it automatically launches rythmbox.. and to make it worse, if I try to close rythmmbox it automatically opens it back up! Any ideas on how to fix this? (The text shows on conky just fine though...)

LOL I just discovered the same thing this morning. Easy fix;

```

${exec rhythmbox-client --no-start --print-playing}

```

---

### Post by GSF1200S on 2007-04-12
> **reclusivemonkey said:**
> LOL I just discovered the same thing this morning. Easy fix;

```

${exec rhythmbox-client --no-start --print-playing}

```

Lol.. Works great.. I dont suppose theres a way to have it say "no song playing" or "none" when rythmbox is closed is there? Im guessing this would be a "If" statement, so maybe its just too much of a pain... Thanks alot for your help.. I never thought of python. :smile:

---

### Post by GSF1200S on 2007-04-12
> **reclusivemonkey said:**
> LOL I just discovered the same thing this morning. Easy fix;

```

${exec rhythmbox-client --no-start --print-playing}

```

Wow.. I just noticed this one.. I dont suppose there is any way to make the words wrap? Haha, I feel like im picking teeth at this point- after all, you didnt sign a service contract once you decided to help](*,)

---

### Post by reclusivemonkey on 2007-04-12
> **GSF1200S said:**
> Wow.. I just noticed this one.. I dont suppose there is any way to make the words wrap? Haha, I feel like im picking teeth at this point- after all, you didnt sign a service contract once you decided to help](*,)

No problem. I have Rhythmbox and Conky myself, so its no biggie.

Firstly, in order to get a "No song playing" message you would have to write a small script and then exec this from conky. I might be able to knock something up today, but I am at work right now. As for wrapping the text, I am not sure about this. There may be a function in conky that will handle this, although you might also be able to work it into the script.

---

### Post by Forceflow on 2007-06-04
This script does it for me:

```
#!/bin/bash

run=${ ps -el | grep rhythmbox}
if [ -z "$run" ]; then
out=$( rhythmbox-client --no-start --print-playing)
cut=$( echo $out | cut -c 0-30)
echo $cut
fi
```

Checks for running rhythmbox, and cuts the now-playing output at 30 chars.

---

### Post by Gonzell on 2007-07-14
Thank you so much for posting that simple command. I've been trying to figure out how to control rhythmbox using console commands for such a long time. For example, I've been trying:

rhythmbox --play-pause

and all along, I just needed to add -client to it, lol.


Thanks man!

---

### Post by nan0meter on 2007-07-14
If you want this now playing message to be updated every x seconds then use this command instead of exec. Where 30 is the number of seconds I believe. For further reference about execi check this site: [http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html")

```
${execi 30 rhythmbox-client --print-playing}
```

---

### Post by lajja on 2007-08-11
Is there a way to play/pause/next/previous songs in terminal for Rhythmbox?
Found this
[http://live.gnome.org/RhythmboxPlugins/WritingGuide#head-7cc2af3615038516ef1d59012df6a9d19b83ee18](http://live.gnome.org/RhythmboxPlugins/WritingGuide#head-7cc2af3615038516ef1d59012df6a9d19b83ee18)

..Which didn't help me at all.

What I'm trying to do is control buttons in the panel.
It's "custom application lauchers" with icons.

I'm a newbie btw.

Thanks.

---

### Post by Haegin on 2007-09-03
> **lajja said:**
> Is there a way to play/pause/next/previous songs in terminal for Rhythmbox?
Found this
[http://live.gnome.org/RhythmboxPlugins/WritingGuide#head-7cc2af3615038516ef1d59012df6a9d19b83ee18](http://live.gnome.org/RhythmboxPlugins/WritingGuide#head-7cc2af3615038516ef1d59012df6a9d19b83ee18)

..Which didn't help me at all.

What I'm trying to do is control buttons in the panel.
It's "custom application lauchers" with icons.

I'm a newbie btw.

Thanks.

Yes - read the man page for rhythmox-client:
```
man rhythmbox-client
```

Basically:
```
rhythmbox-client --play
```
```
rhythmbox-client --pause
```
```
rhythmbox-client --pnext
```
```
rhythmbox-client --previous
```
```
rhythmbox-client --play-pause
```

To stop it from launching rhythmbox from opening when you click a button just add the --no-start option.
```
rhythmbox-client --no-start --play
```

For those people who are using this with conky it is worth looking into the --print-playing-format option which gives great control over the output.

---

### Post by Moezzie on 2008-02-07
Im looking into controlling Rhythmbox remotely from another computer, and since rhythmbox-client works through the terminal i thought that would work great together with ssh. 
As i found out it doesn't...

From what i understand X doesnt work great together with ssh. I keep getting errors like:```

user@media:~$ rhythmbox-client --no-start --next

(rhythmbox-client:8735): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus 
session: Autolaunch error: X11 initialization failed.

```
Seems like ssh cant use X on remote systems. Ive had this problem with other applications to. Everything works fine if i do it locally though.

I tried a to writet this little python script, but it just produces the same error
```

# nextSong.py
import os

os.system("rhythmbox-client --next")
#end
```
Does anybody have any suggestions? It would be great not have to stand up and walk across the room every time a bad song comes on(which is pretty often :p ).

---

### Post by ryniek on 2008-07-21
I've got other problem. I've got that entry in Conky: ```
${exec rhythmbox-client --print-playing}
``` but if i turn on Conky, console shows that: ```
Rhythmbox-WARNING* : The player's position is unavailable
``` 
It shows correctly, the actual song's but it's annoying and conky istn't starting with system by that (i think so).
What i must to do?

---

