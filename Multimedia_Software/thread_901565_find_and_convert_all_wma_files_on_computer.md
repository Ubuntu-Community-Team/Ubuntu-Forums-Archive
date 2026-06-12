---
title: "find and convert all wma files on computer"
date: 2008-08-26
forum: Multimedia Software
---

### Post by tom_eaton on 2008-08-26
Hi all,

I'm trying to sort out my music collection, and I want to convert all the wma's I have to mp3. I've found a couple of scripts that do this, but you have to manually point it at each directory to make it work. Is there a way I can find ALL wma files regardless of directory, convert them to mp3 and delete the old wma?

Thanks

Tom Eaton

---

### Post by tech9 on 2008-08-26
> **tom_eaton said:**
> Hi all,

I'm trying to sort out my music collection, and I want to convert all the wma's I have to mp3. I've found a couple of scripts that do this, but you have to manually point it at each directory to make it work. Is there a way I can find ALL wma files regardless of directory, convert them to mp3 and delete the old wma?

Thanks

Tom Eaton

not sure about a script off hand to do it all at once, but you could install soundkonvertor to convert all your wma to mp3

---

### Post by lintoolman on 2008-08-27
Assuming all of your wma files are in a single directory structure you could use the '[find]("http://linux.die.net/man/1/find")' command to generate a list of directories for example:

```
find music -type d
```This 'find' command should list all directories underneath the 'music' directory.  

If you have a command line converter, you could use the -exec switch on 'find' to execute the command on each directory containing the wma files.   For clarity and testing, you might want to put the command line for conversion into a simple script and then execute the script with the find command something along the lines of:

```
find music -type d -exec convert_script '{}' \;
```Hope this helps.

---

