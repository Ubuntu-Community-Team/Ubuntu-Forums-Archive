---
title: "ffmpeg for multiple files"
date: 2011-11-18
forum: Multimedia Software
---

### Post by ExpL0it0R on 2011-11-18
Hi all. I want to convert multiple files with ffmpeg but i need the names to be changed into mp3 after conversion with basenames each. The command i am using is;

```
ffmpeg -b 192k -i file file.mp3
```

But i dont know how to integrate the basenames into the command. Thanks for any help.

---

### Post by nothingspecial on 2011-11-18
Pass them to a variable

If they are all in the same  directory with nothing else in it then

```
for f in *; do ffmpeg -b 192k -i "$f" "$f".mp3; done
```

---

### Post by ExpL0it0R on 2011-11-18
Thank you it worked but it takes also the extension as basename.

---

### Post by nothingspecial on 2011-11-18
> **ExpL0it0R said:**
> Thank you it worked but it takes also the extension as basename.

Ah, you didn't mention the originals had extensions. Ok assuning the extension is .flac

```
for f in *; do ffmpeg -b 192k -i "$f" "${f/.flac/}".mp3; done
```

Change it to your needs.

---

### Post by ExpL0it0R on 2011-11-18
Thank you !

---

### Post by nothingspecial on 2011-11-18
No problem :)

---

### Post by Lampi on 2011-11-18
thanks nothingspecial,

I noticed "for" has problems when input files contain one or more whitespaces, I solved this by changing the internal field separator $IFS:

```
old_IFS=$IFS ; IFS=$'\n' ; for file in Music/*.aac ; do echo "${file/.aac/}.mp3" ; done ; IFS=$old_IFS
```

This runs fine and will print all files with mp3 instead of aac - but is there a better way to avoid changing IFS back and forth?

---

### Post by Lampi on 2011-11-18
thanks nothingspecial,

I noticed "for" has problems when input files contain one or more whitespaces or an ampersand, I solved this by changing the internal field separator ($IFS):

```
old_IFS=$IFS ; IFS=$'\n' ; for file in Music/*.aac ; do echo "${file/.aac/}.mp3" ; done ; IFS=$old_IFS
```

This runs fine, but is there a better way to avoid changing IFS back and forth?

---

### Post by sisco311 on 2011-11-18
> **Lampi said:**
> thanks nothingspecial,

I noticed "for" has problems when input files contain one or more whitespaces or an ampersand, 



No. Each filename that's matched by the *.acc glob will be treated as a separate word, and the loop will iterate once per filename.

---

### Post by nothingspecial on 2011-11-18
Troubles happen when you use it in conjuction with the find command, are you doing that?

Anyway sisco311 is here so I'll leave him to it.

---

### Post by Lampi on 2011-11-18
arrh - sorry!

I misread the error output :rolleyes: - this had nothing to do with special characters

Sorry for the unnecessary whoops and for the double post!

---

