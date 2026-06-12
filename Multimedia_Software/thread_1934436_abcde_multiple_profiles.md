---
title: "abcde multiple profiles"
date: 2012-03-02
forum: Multimedia Software
---

### Post by Steeperton on 2012-03-02
I have abcde set up with abcde.conf to rip to .ogg, and it all works perfectly (using info taken from [http://www.andrews-corner.org/abcde.html]("http://www.andrews-corner.org/abcde.html")). 

However, every now and then, I need to rip to mp3 instead. Is there any way to have my abcde.conf set up with multiple profiles?

So, when running abcde, I either get asked which profile to run, or I can run .ogg as default, but pass an argument when I want to do it as MP3? 

something like:

```
abcde
``` encodes in .ogg as normal from abcde.conf
```
abcde -mp3
``` encodes in .mp3 with all the options I have set for MP3 in abcde.conf

Is that possible?

---

### Post by nothingspecial on 2012-03-02
Sure, make another conf file named .abcde_mp3.conf (you can call it whatever you like but that's what I use). Put all your mp3 options in that file.

Then the command would be

```
abcde -c ~/.abcde_mp3.conf
```

I have one for flac, ogg and mp3, then I have set some aliases. In my .bash_aliases file I have these lines


```
#Cd ripping/playing
alias cd2flac='abcde -c ~/.abcde_flac.conf'
alias cd2ogg='abcde -c ~/.abcde_ogg.conf'
alias cd2mp3='abcde -c ~/.abcde_mp3.conf'
```

So for mp3 I would just type

```
cd2mp3
```

or ogg

```
cd2ogg
```

and so on.

---

### Post by andrew.46 on 2012-03-02
Nice idea with the bash aliases, can I pilfer that for the abcde web page that Steeperton has mentioned?

---

### Post by nothingspecial on 2012-03-02
> **andrew.46 said:**
> Nice idea with the bash aliases, can I pilfer that for the abcde web page that Steeperton has mentioned?

Of course you can, where do you think I got the basis of my configs from :D

---

### Post by Steeperton on 2012-03-02
Spot on!

Thanks all - solved!

---

