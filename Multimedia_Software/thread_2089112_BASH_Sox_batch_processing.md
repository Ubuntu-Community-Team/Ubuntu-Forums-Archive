---
title: "BASH: Sox batch processing"
date: 2012-11-28
forum: Multimedia Software
---

### Post by Valpskott on 2012-11-28
Soo, I wanted to even out the volume of several mp3:s via the command-line.

```
find . -maxdepth 1 -iname '*.mp3' -type f -print0 | xargs -0 -t -r -I {} sox {} Compressed/{} compand 0.3,1 6:&#8722;70,&#8722;60,&#8722;20 &#8722;5 &#8722;90 0.2
```

I get the error
```
sox FAIL compandt: syntax error trying to read transfer function value
```


My guess is that sox have trouble with handling the spaces in the filenames.
Any suggestions to fix this or a better command-line tool for the job would be greatly appreciated.

---

### Post by Lars Noodén on 2012-11-28
Can't you enclode the braces in quotes?  "{}" 
That should deal with the spaces in the file names.

---

### Post by Valpskott on 2012-11-28
> **Lars Noodén said:**
> Can't you enclode the braces in quotes?  "{}" 
That should deal with the spaces in the file names.

I appreachiate the help. How ever, I misled you with my faulty assumption. It was the parameters of the compression that was the reason for the error message.

Marking this as solved.

---

