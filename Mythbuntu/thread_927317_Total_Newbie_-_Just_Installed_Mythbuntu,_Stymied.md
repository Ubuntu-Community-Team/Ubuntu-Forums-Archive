---
title: "Total Newbie - Just Installed Mythbuntu, Stymied"
date: 2008-09-22
forum: Mythbuntu
---

### Post by mance8 on 2008-09-22
mostly a windows guys, but have years of some linux experience.  been impressed with ubuntu recently.

bought an HD-5500, came today.  just plugged it into my 2 yr old Pundit P1-AH1, ran Mythbuntu 8.04 install

everything looked good, install seemed to go well, until I hit Watch TV.  nothing.  that button does not respond.

even though I'm a geek I was looking for a more successful dumbuser experience.  now it looks like I'm going to have to get my hands dirty ;-)

where do I go to diagnose this?  I can use a terminal, but I can't find any of the guides or tutorials where someone who is stuck as early on as me can know where to go.  I can't tell if it's broken or if I just don't know how to use it.  I thought it detected my card by name.

fwiw, also, I have a homemade hdtv antenna and I also signed up for schedules direct.  thought I successfully input that info, chose my source, and my guide with username and passwrd in the config gui, but just dont know.  help.

if I'm just ignorant please point me to the right repository of knowledge.

thanks.

---

### Post by axelsvag on 2008-09-23
Have you been going throw the steps in the backend setup?

---

### Post by false_apology on 2008-09-23
Any clues in /var/log/mythtv/mythfrontend.log? I got this same problem originally, and it turns out I needed to load special firmware for the ATSC card I was using, and the log told me exactly that.

---

### Post by newlinux on 2008-09-23
pchdtv 5500 should work out of the box. This probably a configuration issue. Can you tell us more about how you set it up in the backend?

Did you use the DVB driver in creating the card?
Did you setup an input source and associate it with this card?
Did you run a scan and lock onto any channels?

BTW, I too have a pundit P1-AH1. Pretty nice little box.

---

### Post by mance8 on 2008-09-23
thanks guys, you've given me lots to try.  am at work but will try that log when I get home and see what it says.

it saw the card when I set up the capture device, at least it came up be default, but I do not recall seeing or choosing a DVB option.  although now that you mention it I did read before I started that that's the driver I'm supposed to use so I need to go see if I can set that there.

I set the source to the service I just subscribed to, but I do not recall if it made it clear that I was binding that source to that capture device.  the menus didn't give me an OK to progress forward, I had to keep escaping to go back.

I do not recall seeing anywhere where I could scan for channels but perhaps that because I didn't do the capture and source part right?

thanks again and I will try tonight and let you know.  

and I like your Deathstroke avatar.  I haven't read Teen Titans since the Reagan era ;-)

---

### Post by mance8 on 2008-09-23
You guys are great!  But now I have new problems ;-(

looked in the log mentioned above, but did not see anything that meant anything to me.  meaning, there was lots of stuff there, but just because it says it can or cannot do something, I don't know if those are errors or not.

however I went back and think I figured out just enough of the mythtv backend setup to be dangerous.  I set it to DVB and I got the EPG and the capture card to be assigned to each other.  (abandoned my home made antenna that got nothing and switched to plain rabbit ears and) scanned the channels and...

Wow!  TV came in.  Yay!  Thanks guys.

but now I'm having (what I hope) are reception problems.  I can sometimes get one channel on startup and then I change to another channel and then the interface freezes.  I have to CTRL+ALT+Backspace to get out and then go back in.

I hope to troubleshoot this with a better antenna or better antenna placement.  if your patience permits I have three questions:

1. is it normal for the mythtv front end to totally freeze when struggling with weak hdtv signals?

2. is there a better way to kill the front end than CTRL+ALT+Backspace?  I have a feeling I'll be doing this a lot while I figure this out ;-)

3. what is a normal signal strength for a channel?  I was seeing stuff in the 40's and 60's.

thank you very much in advance for your help.  I know the side effect of having your distro gain popularity is also to have it include less savy consumers

---

### Post by mance8 on 2008-09-25
It works!  Wahoo!

It was all just reception issues.  I also figured out that double escape quits the front end without me having to kill X.

Now I need to do some work to get a better antenna and better placement.  My best channel only comes in at 78% with rabbit ears.  But it was good most of the time and I was able to pause, fast forward, rewind, record, EPG, everything.  This is great.  Now all I need to do is order my Streamzap remote.

Well done to the MythTV and Mythbuntu teams!  Very nice work.

And thank you guys here for your help.  The community rocks!

---

