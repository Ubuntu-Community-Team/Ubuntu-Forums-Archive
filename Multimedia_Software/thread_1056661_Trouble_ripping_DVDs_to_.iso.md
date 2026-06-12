---
title: "Trouble ripping DVDs to .iso"
date: 2009-02-01
forum: Multimedia Software
---

### Post by pedrogent on 2009-02-01
hi all.

i'm having a hell of a time ripping dvds to .iso images. i've had a lot of success doing this in the past. for the life of me, i can't work out what it is i'm doing wrong?

is it folder permissions? a broken optical drive? the wrong program?

i use the gnome tool to copy to an image rather than a disc and it all seems to be going well until it just stops and says that the job is complete but all that has been produced is a very small .iso (e.g. 512 mb).

any ideas?

---

### Post by andrew.46 on 2009-02-03
Hi,

The classic way to rip an *unencrypted* dvd to iso is with dd:

```
dd if=/dev/dvd of=chosen_name.iso bs=2048
```

I am not familiar with the 'gnome' method you have mentioned I'm afraid.

Andrew

---

### Post by pedrogent on 2009-02-03
by the gnome method i mean:

[LIST]
[*]i'm in ubuntu
[*]i pop in a dvd
[*]it shows up on my desktop (i.e. it's now mounted)
[*]i right-click on it
[*]i select 'copy disc'
[*]i pull down the drop-down box to 'copy disc to: file image'
[*]i press 'write'
[*]i select the location i would like the .iso to be written to
[*]i press 'ok'
[/LIST]

---

### Post by andrew.46 on 2009-02-03
Hi perogent,

> **pedrogent said:**
> by the gnome method i mean:

[LIST]
[*]i'm in ubuntu
[*]i pop in a dvd
[*]it shows up on my desktop (i.e. it's now mounted)
[*]i right-click on it
[*]i select 'copy disc'
[*]i pull down the drop-down box to 'copy disc to: file image'
[*]i press 'write'
[*]i select the location i would like the .iso to be written to
[*]i press 'ok'
[/LIST]

Looks too complicated :-). Did you try dd? This will produce an iso image in the directory from which the command is issued so perhaps:
```

cd $HOME/Desktop
```

first?

Andrew

---

