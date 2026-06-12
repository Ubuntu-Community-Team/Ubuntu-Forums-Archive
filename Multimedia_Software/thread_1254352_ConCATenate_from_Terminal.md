---
title: "ConCATenate from Terminal"
date: 2009-08-31
forum: Multimedia Software
---

### Post by distortedecho on 2009-08-31
Hi,

I'm trying to join AVI files using, from the terminal:

cat 1.avi 2.avi > combined.avi

My files seem to join. They are both 700MB each, and the combined avi is 1.4GB as expected. However, when played back it's still only 1.avi

What am I missing?

---

### Post by wojox on 2009-08-31
Install mplayer and mencoder.

```
cat file.avi file2.avi file3.avi > joined-file.avi
mencoder joined-file.avi -o final-output.avi -forceidx -ovc copy -oac copy
```

---

### Post by distortedecho on 2009-09-01
Thanks.

What does the below mean, is it an output or an additional or alternative command?

```
mencoder joined-file.avi -o final-output.avi -forceidx -ovc copy -oac copy
```

---

### Post by serfcx on 2009-09-01
> **distortedecho said:**
> Thanks.

What does the below mean, is it an output or an additional or alternative command?

```
mencoder joined-file.avi -o final-output.avi -forceidx -ovc copy -oac copy
```

This is the command to run in terminal on the file created from the cat command which will result in the output file "final-output.avi" - rename as you like.
I have used the same but with -noidx option in place of -forceidx to satisfactory effect.

---

