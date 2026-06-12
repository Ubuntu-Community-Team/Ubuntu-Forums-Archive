---
title: "Mythbuntu, MythTV and User Jobs"
date: 2011-09-14
forum: Mythbuntu
---

### Post by drumz on 2011-09-14
I've configured a custom user job to be executed after a recording is done.  It appears that MythTV is launching my script but it appears that the script is not executing.

Here's a sample entry from the MythTV log:

```
2011-09-14 18:51:43.359 JobQueue: Started /usr/bin/test_job.sh %FILE% for "The King of Queens":"Soft Touch" recorded from channel 1247 at 2011-09-14T18:00:00
2011-09-14 18:51:43.472 JobQueue: Finished "The King of Queens":"Soft Touch" for 1247 at 2011-09-14T18:00:00 recorded from channel %3
```

The simple (and very dumb at this point) test script has the following:

```
#!/bin/bash
echo "foo" >> /tmp/mythjob2_data.txt
echo $1 >> /tmp/mythjob_data.txt
```

If I manually execute the script it works fine.  If I 'sudo bash' then 'su - mythtv' and execute the script it works.

What am I missing?

---

### Post by klc5555 on 2011-09-16
Just a guess: 

The backend probably doesn't use bash and may not have a path set. So possibly eveything needs to be invoked with full paths specified, e.g. "/bin/echo"

---

### Post by thatguruguy on 2011-09-16
A mythbuntu backend that doesn't have bash installed? RLY?

To me, it sounds more like a permissions problem.

---

### Post by klc5555 on 2011-09-16
> **thatguruguy said:**
> A mythbuntu backend that doesn't have bash installed? RLY?

To me, it sounds more like a permissions problem.

I didn't say the machine doesn't have bash _installed_. The original poster ran his bash script from the CLI in bash.

In a more expansive form, what I wished to convey was that mythbackend (the application) doesn't necessarily use bash as its shell, and what it uses doesn't necessarily have a path set. So all paths in and pertaining to the script may need to be made fully explicit.

---

### Post by drumz on 2011-09-18
It ended up being something brain-dead simple - and based on some other posts I suspect other people have done the same exact thing:

When I added the job, I added the call to the script to the 'Description' field, not the field where you were supposed to enter it.  The field where you were supposed to enter the call to the external script was blank.

When adding it, I was on my laptop and connecting remotely to my backend server so it's possible in my rush I misread the screen or it didn't render properly I'm not sure at this point.  I just checked now and everything displayed correctly and was clearly labelled.

I discovered my mistake because I also use MythWeb and happened to go into the maintenance area on it where I found my mistake and corrected it.  (Based on other posts you may have to include full paths to binaries, I already had made that change during my previous debugging and left that alone based on you other posts and yours.)

So for anyone whose User Job in MythTV is being called but doesn't seem to be executing - make sure you have the entries entered into the correct fields!

---

