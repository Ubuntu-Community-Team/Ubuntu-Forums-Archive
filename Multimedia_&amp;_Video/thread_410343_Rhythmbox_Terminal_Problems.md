---
title: "Rhythmbox Terminal Problems"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by Browzilla on 2007-04-15
I'm trying to get some terminal commands to work with Rhythmbox, and they don't want to.  I've got the app running fine itself, on Xubuntu, but it doesn't want to work when I try to set up keyboard shortcuts, or in the terminal directly.  

A **man rhythmbox** returned the following, edited to the parts I'm attempting to use:

```

OPTIONS
       Rhythmbox accepts some options common to all X and GNOME  applications,
       like  -display  displayname.  These are not included in the list of op&#8208;
       tions below. You can use the --usage argument to show the complete list
       of accepted options.



        --play-pause
              Toggle play/pause mode

       --focus
              Focus the running player

       --previous
              Jump to previous song

       --next Jump to next song

```

Nothing to amazing, right?  I went over to the keyboard shortcuts menu, and added a new one.   
Under command I put 
```
rhythmbox --next
```
And did the same for the pause and previous functions.  Then I set the shortcuts, and tried them.  And none worked.  

So I figured I might've done something wrong, and tried the commands directly in the terminal instead.  Still nothing.
```

browzilla@masashi:~$ rhythmbox --next
Unknown option --next
Run 'rhythmbox --help' to see a full list of available command line options.

```

Anyone know how to make this work?

---

### Post by Browzilla on 2007-04-15
C'mon, someone's gotta know.  Rhythmbox is bugging me without hotkeys.

---

### Post by reclusivemonkey on 2007-04-16
Use

```

rhythmbox-client

```

---

### Post by kinson on 2007-04-23
> **reclusivemonkey said:**
> Use

```

rhythmbox-client

```

Thanks :) I just upgraded to Feisty (from Dapper), and in the man files, I couldn't find any "--play-pause" option, which I use for my alarm script. So it was bugging me a little.

So now I use this :
```

rhythmbox-client --play-pause

```

But if I may ask, whats with this "client" thingy? Is it a different version of Rhythmbox?

Cheers,
Kinson

---

