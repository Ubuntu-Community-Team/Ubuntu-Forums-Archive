---
title: "How to assign underscore _ or dash/minus - with lirc ir remote"
date: 2011-05-27
forum: Mythbuntu
---

### Post by davidstoll on 2011-05-27
Since some of my channels have either an underscore or a dash, I need to be able to send that signal with my MCE ir remote.

I have made a custom ir file and I can assign buttons, so I am familiar with the process, but I'm thinking that because _ and - are special characters, there might be a trick.

I am trying to assign _ and - to Star and Hash (or vise versa).

---

### Post by LowSky on 2011-05-27
Why not just reassign the channel numbers from the channel editor on the back-end.

---

### Post by davidstoll on 2011-05-27
Because there are too many to try and re-learn.  I would rather keep them where they were intended to be named.

I use OTA and there can be (for instance) several channel #3's...i.e. 3_1, 3_2, 3_3...


> **LowSky said:**
> Why not just reassign the channel numbers from the channel editor on the back-end.

---

### Post by azmyth on 2011-05-27
I'm using an OTA tuner with an analog STB. The blaster controls the STB but I don't need to worry about sending the IR signal for OTA since the OTA isn't controlled by a STB.

I would be curious to now how I could use the remote to change to an OTA channel since entering 31 will take me to channel 31 on the STB and not to 3_1 but then agains this is probably the way I would want it to work. I change to OTA through the guide.

---

### Post by davidstoll on 2011-06-01
bump

---

### Post by goffa on 2011-06-02
> **davidstoll said:**
> 

I am trying to assign _ and - to Star and Hash (or vise versa).

So to assign the minus key to the asterix (star) key you could modify your ~/.mythtv/lircrc file with the following

  begin
    prog = mythtv
    button = KEY_ASTERIX
    config = -
  end


You may need to check your /etc/lirc/lircd.conf file to see the exact naming of asterix key or open a terminal type irw and press the star and hash buttons on your remote to determine the exact button names. This name needs to be in the "button = " line in the above code.

---

### Post by davidstoll on 2011-06-02
irw gives me Star and Hash, but unfortunately, it doesn't work.  I even tried with and without the remote line.

I reloaded lirc and mythtv too.
sudo /etc/init.d/lirc restart

begin
    remote = mceusb
    prog = mythtv
    button = Star
    config = -
end

begin
    remote = mceusb
    prog = mythtv
    button = Hash
    config = _
end


> **goffa said:**
> So to assign the minus key to the asterix (star) key you could modify your ~/.mythtv/lircrc file with the following

  begin**
    prog = mythtv
    button = KEY_ASTERIX
    config = -
  end


You may need to check your /etc/lirc/lircd.conf file to see the exact naming of asterix key or open a terminal type irw and press the star and hash buttons on your remote to determine the exact button names. This name needs to be in the "button = " line in the above code.

---

### Post by davidstoll on 2011-06-02
Small clarification:
If I put these entries into my own custom file in ~./lirc/, they don't work...but my other entries do.  The only difference is that my other entries are prog = irexec, not mythtv.

These need to be in the mythtv file...and then they work.

Why can't I call them from another file even if I use prog = mythtv ?  It's referenced in from ~/.lircrc and my other entries work....



> **davidstoll said:**
> irw gives me Star and Hash, but unfortunately, it doesn't work.  I even tried with and without the remote line.

I reloaded lirc and mythtv too.
sudo /etc/init.d/lirc restart

begin
    remote = mceusb
    prog = mythtv
    button = Star
    config = -
end

begin
    remote = mceusb
    prog = mythtv
    button = Hash
    config = _
end

---

### Post by uncle hammy on 2011-06-05
> **davidstoll said:**
> Because there are too many to try and re-learn.  I would rather keep them where they were intended to be named.

I use OTA and there can be (for instance) several channel #3's...i.e. 3_1, 3_2, 3_3...

It's easier to remember multiple separator symbols, rather than "all channels are X-Y or X_Y"?

Why not just do a simple query on MySQL...

```

UPDATE channel SET channum = REPLACE(channum, 'my_old_separator', 'my_new_separator');

```

i.e. if you want all your channels to be dashes....

```

UPDATE channel SET channum = REPLACE(channum, '_', '-');

```

Do that for all your different separators, and then you'll be consistent.

However, I always update lircrc in the ~/.mythtv folder (which is just a symlink to ~/.lirc/mythtv) for my lirc changes, and they always work.

---

### Post by davidstoll on 2011-06-06
Changing all the -'s to _'s (or whatever) is not a huge deal, I can do that in mythweb...although your way is cool...however, I thought LowSky was talking about renumbering 17_1 to 171 or something, especially if there is already a 17...renumbering is not ideal.  Changing the symbol is fine, but I just want to make the pound and/or hash a _ and/or -.  Changing them all to _ or - so they are consistent is fine, but my main drive here is to get a function on my remote to call those characters...which is working now.

The question now, more because I'm just curious, is why didn't the changes in my custom ~/.lirc/custom  file work?  Other functions in my custom file work just fine.  I had to put my Star and Hash functions in the ~/.lirc/mythtv  file for them to work.

Strange.


> **uncle hammy said:**
> It's easier to remember multiple separator symbols, rather than "all channels are X-Y or X_Y"?

Why not just do a simple query on MySQL...

```

UPDATE channel SET channum = REPLACE(channum, 'my_old_separator', 'my_new_separator');

```

i.e. if you want all your channels to be dashes....

```

UPDATE channel SET channum = REPLACE(channum, '_', '-');

```

Do that for all your different separators, and then you'll be consistent.

However, I always update lircrc in the ~/.mythtv folder (which is just a symlink to ~/.lirc/mythtv) for my lirc changes, and they always work.

---

