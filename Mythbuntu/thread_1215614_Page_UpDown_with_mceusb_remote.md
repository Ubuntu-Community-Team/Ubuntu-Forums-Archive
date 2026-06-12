---
title: "Page Up/Down with mceusb remote"
date: 2009-07-17
forum: Mythbuntu
---

### Post by ktmom on 2009-07-17
Everything works great with the remote setup.  But after several hours of reading (the wrong things?), I can not resolve how to configure the channel up/down buttons to actually do a page up/down at least when viewing the program guide and recording and video lists.

I think what I am missing is the MythTV command code, then I can just map the buttons to the correct command.  Is that right?  

Thanks for any pointers.

---

### Post by tgm4883 on 2009-07-17
> **ktmom said:**
> Everything works great with the remote setup.  But after several hours of reading (the wrong things?), I can not resolve how to configure the channel up/down buttons to actually do a page up/down at least when viewing the program guide and recording and video lists.

I think what I am missing is the MythTV command code, then I can just map the buttons to the correct command.  Is that right?  

Thanks for any pointers.

Yea, I hate that as well. What you actually want to do is (and forgive me if this is incorrect, but I am unable to verify this until I get back to my mythbox which isn't going to be until tomarrow)

What you need to do is edit your .mythtv/lircrc and search for the channelup (actually, it may be chup or ch+). Once you find this notice that the command it issues is Up. This should read PgUp. You will need to do this for down as well.

---

### Post by ktmom on 2009-07-17
Thank you very much for the reply.  You got me where I wanted to be.  I hadn't been trying the right combination of abbreviations.

My ~/.mythtv/lircrc points to ~/.lirc/mythtv

I modified  ~/.lirc/mythtv so that the entries for ChanDown and ChanUp look like
```

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

```

---

### Post by tgm4883 on 2009-07-17
That looks good, you will need to restart the frontend for it to work.

---

