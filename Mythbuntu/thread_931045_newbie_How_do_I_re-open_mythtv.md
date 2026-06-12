---
title: "newbie: How do I re-open mythtv?"
date: 2008-09-26
forum: Mythbuntu
---

### Post by StarThorn1 on 2008-09-26
I closed mythtv and now im on the desktop. How do I open it up again without restarting my pc?

---

### Post by volkswagner on 2008-09-26
What version are you running?

For 7.10, go to >Applications>multimedia>mythfrontend

---

### Post by bmwman on 2008-09-26
Or you can type it in a Terminal -"mythfrontend"

;)

---

### Post by tgm4883 on 2008-09-27
I'll assume the question isn't how do I restart the frontend, but rather, how do I restart the frontend when only a remote is attached to the system.  You will need to add something like this to ~/.mythtv/lircrc

```
begin
    remote = mceusb
    prog = irexec
    button = Power
    repeat = 3
    config = start-myth&
end
```

That calls /usr/bin/start-myth (which you need to create), which contains this

```
#!/bin/sh
# Eric Kerby, July 2007

# see if mythfrontend is already running
# if not, start it
if ps ax | grep -v grep | grep mythfrontend > /dev/null
then
echo "Do nothing..." > /dev/null
else
/usr/bin/mythfrontend&
fi

```

---

