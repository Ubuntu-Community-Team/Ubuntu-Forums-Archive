---
title: "A Problem with ripIT creating duplicate rips (closing tray on old disc)"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by zds on 2008-01-12
I'm working with the great ripper ripIT ([http://www.suwald.com/ripit/ripit.html](http://www.suwald.com/ripit/ripit.html)), but I'm having a problem with the loop feature.

For some reason, the tray won't stay open after eject in order to wait for a new disc to be loaded. Once the encoding finishes and the program cycles to wait for the new disc, the tray closes and I get duplicate files (dir name[2], [3], etc).

Anyone familiar with this problem and have any suggestions? I've already tried changing the eject command to the cycle, with no success.

Thanks.

---

### Post by zds on 2008-01-12
So, an update:

Continuing to work this problem, I dug into the source and found this section:

```
else {                         # Close the tray.
   my $closeopt = $cddev if($ejectopt eq '{cddev}');
   $closeopt = "-t " . $closeopt if($ejectcmd =~ /^eject$/);
   $closeopt = $closeopt . " close" if($ejectcmd =~ /cdcontrol/);
   log_system("$ejectcmd $closeopt") if($multi == 0);
}

```

I changed it to:

```
else {                     
}
```

Doesn't solve the problem...

---

### Post by zds on 2008-01-13
The newest beta solves the problem.

---

