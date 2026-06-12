---
title: "mencoder options"
date: 2009-10-27
forum: Multimedia Software
---

### Post by b-boy on 2009-10-27
Hi all

I have a PS3 and it does not play some XVID movies and on one of the forums a guys said if you run the following its should work 
```
mencoder old.avi -oac mp3lame -lameopts br=192 -vf harddup -ovc copy -ffsourcc XVID new.avi
```

he says > only re-encoding the MP3 seems to work

but when I try running the above file i get en error
```
-ffsource is not an MEncoder option
```
Does anyone know what is the correct option?

---

### Post by andrew.46 on 2009-10-27
Hi b-boy,

> **b-boy said:**
> 
```
-ffsource is not an MEncoder option
```
Does anyone know what is the correct option?

The correct option is *-ffourcc XVID*.

Andrew

---

### Post by b-boy on 2009-10-27
> **andrew.46 said:**
> Hi b-boy,



The correct option is *-ffourcc XVID*.

Andrew

thanks Andrew now it says 

```
Exiting... (No output file specified, please see the -o option.)
```


any ideas?

---

### Post by andrew.46 on 2009-10-27
Hi b-boy,

> **b-boy said:**
> ```
Exiting... (No output file specified, please see the -o option.)
```

My apologies, I did not look at the *full* commandline. You need to specify the output file as follows:

```
-o new.avi
```

If you have a look at the bottom of the man page for MEncoder, under 'EXAMPLES OF MENCODER USAGE' you will see a few examples that should demonstrate how the syntax runs in general.

Andrew

---

### Post by b-boy on 2009-10-27
> **andrew.46 said:**
> Hi b-boy,



My apologies, I did not look at the *full* commandline. You need to specify the output file as follows:

```
-o new.avi
```

If you have a look at the bottom of the man page for MEncoder, under 'EXAMPLES OF MENCODER USAGE' you will see a few examples that should demonstrate how the syntax runs in general.

Andrew

thanks

---

