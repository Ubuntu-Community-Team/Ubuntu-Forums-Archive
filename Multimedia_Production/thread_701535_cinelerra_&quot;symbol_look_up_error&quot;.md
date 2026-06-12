---
title: "cinelerra &quot;symbol look up error&quot;"
date: 2008-02-19
forum: Multimedia Production
---

### Post by templa edhel on 2008-02-19
so i tried to install cinelerra using [this]("http://www.ubuntugeek.com/howto-install-cinelerra-in-ubuntu-gutsy-gibbon.html") guide. it didnt show up in the applications menu so i went to synaptic and found it there. when i installed with synaptic it showed up in applications but wouldnt open when i clicked on it. i opened a terminal and typed ```
cinelerra
``` it didnt open but it gave me this ```
cinelerra: symbol lookup error: /usr/lib/libguicast.so.1: undefined symbol: glDeleteShader

```

what does it mean???

thanks for any help.

---

### Post by wawarren on 2008-02-19
It probably wants a different version of that library.  Either older or newer, it's hard to say.  

Unless somebody has a more elegant answer, Here's a few things I would do.  

Find the library (usually just a symlink) being refrenced.  type this

```
nm -D libguicast.so.1
```

This will give you a big list of all symbols being defined in this particular lib.  Most likely you won't find glDeleteShader.  

Next, I would find the Cinelerra installation directory and check if it came with it's own library files.  Sometimes applications come with their own libs, and you've usually got to source a setup script of some type before launching the app.  Those scripts usually set LD_LIBRARY_PATH to their own libs among other things. 

You can do this yourself if the above isn't the case.  This means hunting down the library file with the symbol you need on google, then placing it in a safe place.  (ie. NOT in /usr/lib)  

Then you could re-name the applications executable to something like cinellera.orig (make a backup first) and create a wrapper script named cinelerra.  chmod u+x to make it execute.  

Something like this
```
#!/bin/bash
export LD_LIBRARY_PATH=/my/custom/libguicast
exec /some/dir/cinelerra.orig
```

I've had to do all sorts of hacky voodoo like this to make things work for me, but maybe somebody else will respond with something easier.  I've honestly never used cinelerra.

---

### Post by templa edhel on 2008-02-19
lol i think this may be the problem

i entered  ```
nm -D libguicast.so.1

```

and it said n```
m: 'libguicast.so.1': No such file

```

any ideas?

---

### Post by wawarren on 2008-02-20
you need to cd into /usr/lib before using that command.  

sorry I didn't specify that.

Also, most of the time when symbols are missing Ubuntu will only tell you about the FIRST one. Meaning you could be missing tons of them, or just one.  To figure this out, you need to cd into the directory containing cinelerra's executable file.  and do 

ldd -v ./cinelerra  (or whatever it's called)

-v = Verbose, which will spit out everything including all details.  

**edit: ** 

After a quick look.  check these out

[http://ubuntuforums.org/showthread.php?t=625567](http://ubuntuforums.org/showthread.php?t=625567)

[http://www.peter-v.com/106/how-to-install-cinelerra-on-ubuntu-710-gutsy/](http://www.peter-v.com/106/how-to-install-cinelerra-on-ubuntu-710-gutsy/)

Both mention your problem. However, I brief read through some of those posts mentions Cinelerra using Open GL 2, which may not be supported by ATI drivers (if thats what you use).  Somebody mentioned a version compiled without Open GL 2, or compiling it yourself.  Everything was in Italian, so I couldn't read it much :)

Info on compiling it. 
[http://ubuntuforums.org/archive/index.php/t-586370.html](http://ubuntuforums.org/archive/index.php/t-586370.html)

The supposed link to the non-Open GL 2 version (Italian I think?)
[http://www.akirad.net/](http://www.akirad.net/)

---

### Post by templa edhel on 2008-02-20
thanks alot. ya when i disabled the ati card via restricted drivers it worked fine. iv actually been experimenting with blenders composite nodes and sequence editor and i like those. so cinelerra works now but i might not use it lol. and i would like to use my graphics card. thanks for all the help.:)

---

### Post by cotcot on 2008-02-20
Compile it from source. The output of the ./configure command is very helpful in finding the missing deps. There are not that much.
Make sure you hve the .dev packages installed. A couple of errors in make can occur but google gave me answers on that. I have cinelerra complied on 32 bit and 64 bit, OpenGL enabled (recommended) with nvidia graphics card. Works all fine.

---

