---
title: "turning on pc speaker beep only works for root"
date: 2010-10-18
forum: Multimedia Software
---

### Post by eli_12345 on 2010-10-18
Hi,
i'm running Ubuntu 10.04 server and want to turn on the pc-speaker warning-beep. I commented out the line  in /etc/modprobe.d/blacklist.conf:

#blacklist pcspkr

The beep is now working for root. But somehow it won't work if i log in as a normal user. Has anyone an idea how this could be solved?

(i don't know why, but if i install beep the beep-command works for all users...unfortunately beep seems not to make a warning sound in all cases so this is no solution for me)

---

### Post by Lomaxx on 2010-11-09
Hello eli.

You maybe have the same issue that i had till a few moments ago. While searching for a solution i browsed the Internet and stumbled across this thread. Then, after finding no real solution, i decided to read the man-page of beep. Yes, they sometimes really are helpful. ;) Here is a quote from it:

```

       Some  users will encounter a situation where beep dies with a complaint
       from ioctl().  The reason for this, as Peter Tirsek was nice enough  to
       point  out  to  me, stems from how the kernel handles beep's attempt to
       poke at (for non-programmers: ioctl is a  sort  of  catch-all  function
       that  lets  you  poke at things that have no other predefined poking-at
       mechanism) the tty, which is how it beeps.  The  short  story  is,  the
       kernel checks that either:

       - you are the superuser

       - you own the current tty

       What  this means is that root can always make beep work (to the best of
       my knowledge!), and that any local user can make beep work, BUT a  non-
       root  remote user cannot use beep in it's natural state.  What's worse,
       an xterm, or other x-session counts, as far as the kernel is concerned,
       as 'remote', so beep won't work from a non-priviledged xterm either.  I
       had originally chalked this up to a bug, but there's actually nothing I
       can  do  about  it,  and it really is a Good Thing that the kernel does
       things this way.  There is also a solution.

       By default beep is not installed with the suid bit  set,  because  that
       would  just  be  zany.  On the other hand, if you do make it suid root,
       all your problems with beep bailing on ioctl calls will magically  van-
       ish,  which  is  pleasant,  and the only reason not to is that any suid
       program is a potential  security  hole.   Conveniently,  beep  is  very
       short, so auditing it is pretty straightforward.

       Decide  for yourself, of course, but it looks safe to me - there's only
       one buffer and fgets doesn't let it overflow,  there's  only  one  file
       opening, and while there is a potential race condition there, it's with
       /dev/console.  If someone can exploit this race by replacing  /dev/con-
       sole, you've got bigger problems.  :)

       So  the  quick,  only,  and likely safe solution if beep is not beeping
       when you want it to is (as root):

       # chmod 4755 /usr/bin/beep

       (or wherever you put it)

       The one snag is that this will give any little nitwit  the  ability  to
       run  beep successfully - make sure this is what you want.  If it isn't,
       a slightly more complex fix would be something like:

       # chgrp beep /usr/bin/beep

       # chmod 4750 /usr/bin/beep


       and then add only beep-worthy users to the 'beep' group.

```

So again: After executing

```
chmod 4755 /usr/bin/beep
```

as root, it worked for me. I hope this will solve the issue for you too.

Have a nice lifespan,
Lomaxx

EDIT: I forgot to mention that i am using Gentoo and not Ubunutu. So you might have a different manpage and/or beep-command. I read on the Net that there is a "-e" parameter for "beep", but for the Gentoo-version of beep this does not work. Still this solution might be working for you.

---

### Post by wayover13 on 2011-01-05
Thanks for providing the resolution for this problem, Lomaxx. I've actually run across and implemented this solution before. But when I do system updates settings on relevant binaries get changed. Then, I forget what the problem was and how I fixed it. So I've finally revisited and fixed the problem again by reviewing your post in this thread. Hopefully that means I'll remember next time it happens :) .

James

---

