---
title: "FYI: repeat in xmms2"
date: 2008-10-20
forum: Multimedia Software
---

### Post by ljungkvist on 2008-10-20
Although it says so on the official homepage there is no intuitive repeat commando in the xmms2 client (it seems like there was one once). I spend alot of time with my friend google searching, without finding something (which suprised me, i mean this is a fundamental thing, repeat!). Anyways, at last i found the solution. And i thought i'd write it here for future reference of others (and myself if i manage to forget...).

It appeared that xmms2 has a 'config' command which lets you customize pretty much everything you could imagine. Among all of these things, there is the playlist.repeat_all variable which lets you turn this feature on (there is also a playlist.repeat_one). So what i did was write a short shell script that lets you toggle it on/off

```

function xmrepeat
{
    REP_VAR=$( xmms2 config playlist.repeat_all )
    xmms2 config playlist.repeat_all $[ ! $REP_VAR ]
}

```
you are more than welcome to comment my solution, i'm really a newbie when it comes to bash scripting.

Odd as it may seem, they haven't made it 'official' as a command. Is there any way to add an option or a flag to a built in function?

---

### Post by nomnex on 2009-12-29
at last:) Thanks

---

### Post by t00r on 2011-09-22
$ nyxmss2 server config playlist.repeat_all 1

---

### Post by nothingspecial on 2011-09-22
And we bid you goodnight, goodnight, goodnight.

---

