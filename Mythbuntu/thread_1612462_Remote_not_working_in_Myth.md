---
title: "Remote not working in Myth"
date: 2010-11-03
forum: Mythbuntu
---

### Post by bawatkins on 2010-11-03
Well after lots of time researching I thought I had it all in place, finally got the remote control detected, recorded a lirc file and can now see the correct keypresses when I do an IRW.
 
Problem I have is this is for some reason not being passed to Myth. When use the remote in Myth, nothing happens. I created a lircrc file and put it in ~/.mythtv/lircrc but there is something missing and I cant find it, very fustrating.
 
The system is on mythbuntu 10.10, any suggestions?

---

### Post by iponeverything on 2010-11-03
is the lircd daemon being being started?

---

### Post by rhpot1991 on 2010-11-03
Use mythbuntu-lirc-generator to generate the proper ~/.lirc files from your working configuration.

---

### Post by bawatkins on 2010-11-04
used mythbuntu-lirc-generator  to create new files as you suggested. Can see I have new files, still get key presses in irw but nothing in myth even after restarting system.

---

### Post by mr_luksom on 2011-02-05
I have been having the exact same issue.

It turns out that the lirc daemon was calling the wrong "remote", and hence the signals were not picked up by mythtv. 

An excerpt from my .lircrc

```

begin
    remote = lircd.conf
    prog = mythtv
    button = KEY_0
    config = 0
    repeat = 0
    delay = 0
end


```

irw output:
```


000000000000000a 01 KEY_STOP lircd.conf.conf


```

The key was, notice how irw was referring to lircd.conf.conf (a non-existent file on my machine?) - this is the remote parameter it was passing. By changing my .lircrc file to include the extra '.conf', all was fixed. I'm sure there is also a way to ensure lircd passes the correct remote parameter, but this works for me.

```


begin
    remote = lircd.conf.conf
    prog = mythtv
    button = KEY_0
    config = 0
    repeat = 0
    delay = 0
end

```

Hope this helps.

---

### Post by mr_luksom on 2011-02-05
Also, mythbuntu-lirc-generator caused nothing but trouble for me. Just lots of empty files included in the main lircrc file.

It's not difficult to make your own lircrc file, I'd just stick with that.

---

