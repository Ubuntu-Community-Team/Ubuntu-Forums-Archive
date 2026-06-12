---
title: "myth programs need &quot; --dump_settings&quot;"
date: 2009-02-19
forum: Mythbuntu
---

### Post by mathog on 2009-02-19
One thing that really strikes me from reading this newsgroup is that, for the purposes of figuring out everybody's problems, it would be a lot easier if all of the myth programs had a switch like this:

```
mythwelcome --dump_settings
mythtv-setup --dump_settings
etc.

```
This would emit the current settings in text form.  Currently people are resorting to summarizing screens and/or posting screen dumps.  All the information is text though.  So it would be a lot easier to spot configuration differences, typos, etc. if we could just run diff to see how "my system differs from your system".

If all of these settings are stored in the myth database then this function could be moved to either a little SQL script or a separate program.  It should of course by default replace passwords with XXXXXXXX or something, to avoid security issues.  This would allow a huge number of threads in this forum to be resolved quickly through:

```
myth_dump_settings >my_settings.txt
diff my_settings.txt your_settings.txt

```
Just a thought.

---

### Post by ian dobson on 2009-02-19
Hi,

You could just use mysql-admin to dump the sql tables.

The problem is that there are a large number of settings (I have over 500 settings just in my settings table.)

Edit: Itwouldn't be that hard to write something in perl. Something like:-
./Dump-settings --all 'All settings
./Dump-settings --channels  'Just channel/multipex data
./dump-settings --host=frontend 'Just settings for host frontend
 
Regards
Ian Dobson

---

