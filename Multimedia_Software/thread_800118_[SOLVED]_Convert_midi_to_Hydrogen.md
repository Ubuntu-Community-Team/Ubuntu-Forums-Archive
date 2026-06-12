---
title: "[SOLVED] Convert midi to Hydrogen"
date: 2008-05-19
forum: Multimedia Software
---

### Post by criptonite on 2008-05-19
I've found a perl script called midi2hydrogen.pl that will convert midi drum tracks to Hydrogens .H2song format.  When I run the script I get the following error report:

Can't locate MIDI.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at midi2hydrogen.pl line 54.
BEGIN failed--compilation aborted at midi2hydrogen.pl line 54.

Does anyone know what MIDI.pm is and how I install it so that the script works?

---

### Post by criptonite on 2008-05-19
If anyone wants to experiment with the script, its attached.

---

### Post by Monicker on 2008-05-19
Looks like a perl module.  It appears to be in the repositories.

sudo apt-get install libmidi-perl
```


Description: read, compose, modify, and write MIDI files in Perl
 This suite of Perl modules provides routines for reading, composing,
 modifying, and writing MIDI files.
```

---

### Post by criptonite on 2008-05-20
Exactly right!  After that I needed to also install Simple.pm.  I found this at cpan.org (should anyone need it.

The midi to hydrogen script works brilliantly, if anyone needs that function.

Thanks for your help

---

