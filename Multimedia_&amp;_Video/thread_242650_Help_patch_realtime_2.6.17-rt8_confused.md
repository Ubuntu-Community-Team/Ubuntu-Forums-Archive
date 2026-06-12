---
title: "Help patch realtime 2.6.17-rt8 :confused"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by thestuckup on 2006-08-23
I have been following the outline found at

[http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption](http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption)

to get the realtime kernel.  So far I am doing ok.  I am new to this stuff so it has taken me a couple tries and re-installs to get where I am at.  I have successfully downloaded the latest kernel source, but then where I get to the part where I patch it;
[COLOR="Red"]
Now, let's patch the kernel source.[/COLOR]

[COLOR="Navy"]cd linux/
patch -sp1 < ../patch-2.6.16-rt26
patch -sp1 < ../kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch[/COLOR]

Mind you I think i've only tried the first patch listed because I anticipated something going wrong. ;)  - so I actually
i changed the directory to /usr/src/linux, and than I did

patch -sp1 < ../patch-2.6.16-rt26

It gave me back that 1 out of 2 hunks failed and crated a file called Makefile.rej, which I assume is just a bunch of unusable trash?

anyway, I can't tell you the exact message it gave me because I didn't have the presence of mind to take note and when I went back to retry it so  I could copy the note, I end up with

[COLOR="Blue"]/usr/src/linux# patch -sp1 < ../patch-2.6.17-rt8
Reversed (or previously applied) patch detected!  Assume -R? [n] y
The next patch would create the file Documentation/DocBook/genericirq.tmpl,
which already exists!  Assume -R? [n] -y
Apply anyway? [n] y
Patch attempted to create file Documentation/DocBook/genericirq.tmpl, which already exists.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/DocBook/genericirq.tmpl.rej
The next patch would create the file Documentation/RCU/proc.txt,
which already exists!  Assume -R? [n]
[/COLOR]


...As you can see I said yes to the first couple in hopes it would take and there would only be a few files I would have to respond yes to - not the case.  It goes on and on and on and if I answer yes it doesn't matter the system rejects it and saves it to a new reject file.

If anybody could help me

PS  This is a new system so not much is on here - it's not a tremendously huge deal for me to reinstall again if necessary.

Thanks

---

