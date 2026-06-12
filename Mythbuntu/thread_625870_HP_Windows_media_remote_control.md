---
title: "HP Windows media remote control"
date: 2007-11-28
forum: Mythbuntu
---

### Post by aznewsh on 2007-11-28
I have this remote and for the most part seems to work well, I would like to tweak a few of the buttons to my preference, is there an easy way to do this?

ch up and ch down seem to skip rather than what they are supposed to do for instance, I would like to start there and gradually modify until the setup works for me.

I know there are already lots of posts like this but I am kinda overwhelmed by all the info.

I had a look at my etc/lirc/lircd.conf file but it contains a bunch of codes that mean nothing to me - perhaps I am at the wrong place?

---

### Post by superm1 on 2007-11-28
The file(s) you want to tweak are:

~/.lircrc
and
~/.mythtv/lircrc

---

### Post by newlinux on 2007-11-28
I recommend you backup your lircrc files first...

When you say ch+ and ch- skip, what do you mean? Do you mean they browse through the channels instead of changing them? If so I believe there is a setting in the frontend (setup->TV Settings->Playback or somewhere around there) that can change this behavior.

---

### Post by aznewsh on 2007-11-28
> **newlinux said:**
> I recommend you backup your lircrc files first...

When you say ch+ and ch- skip, what do you mean? Do you mean they browse through the channels instead of changing them? If so I believe there is a setting in the frontend (setup->TV Settings->Playback or somewhere around there) that can change this behavior.

No I mean they act like a skip button, they skip forward or to put it another way they advance play by a few seconds

---

### Post by aznewsh on 2007-11-28
OK here is the relevant section of those files:

begin
    remote = mceusb
    prog = mythtv
    button = ChanDown
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = ChanUp
    config = PgUp
    repeat = 0
    delay = 0
end

I would guess that I need to bind config to a something different, but what?

:confused:

---

### Post by newlinux on 2007-11-28
Okay, I see.
IIRC, right and left are the buttons that skip forward and back, so change  the config values to right and left or left and right depending on which button you want to skip forward or backward.

e.g.

config = right


config = left

for those two buttons. You'll want to restart the frontend after making those changes.

---

### Post by newlinux on 2007-11-28
Oh wait, I may have changed my keybindings to do that specifically in the key editor, so this may not work...

---

### Post by aznewsh on 2007-11-28
Not quite - I want my channel up and channel down buttons on my remote ti change the channel up and down respectively - sorry for the confusion - right now they are not doing that, they are acting as skip buttons

I suspect that it will actually have to bind two keys since channel change seems to be up & then enter or down then enter

---

### Post by newlinux on 2007-11-28
Them I believe it is simply up and down instead of left and right. Back to my previous post... If they only browse to different channels instead of changing them, then you need to change the setting in your mythfrontend... Again noting that I have changed the default keybindings on my machine, so this might not work for you...

---

### Post by superm1 on 2007-11-28
Actually the upcoming backport of mythbuntu-lirc-generator will map the keys this way.  After it is installed, you can open up MCC and "regenerate" the dynamic button map.

The backport should be arriving within 1-2 days.

---

### Post by aznewsh on 2007-11-29
Will this be an auto-update?

---

### Post by superm1 on 2007-11-29
> **aznewsh said:**
> Will this be an auto-update?
It will be available on gutsy-backports.

Open up Applications->System->Software Sources and make sure you have backports enabled.  As long as you do, you should be notified when it hits your mirror.  It's already on the main archive.ubuntu.com mirror afaik.

---

