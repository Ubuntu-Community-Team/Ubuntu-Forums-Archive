---
title: "Script converting APE + CUE to splitted FLACs"
date: 2009-03-02
forum: Multimedia Software
---

### Post by txust on 2009-03-02
Hi everyone. I only registered to post this script, for I couldn't find anything that does this.
I'm spanish, so this script is in spanish too, but it's easy to understand, I think.
It basically converts an APE + CUE file in several FLAC files and renames and tags them using the information provided by the cue sheet. It also installs any package needed, except mac-port, but tells you how to do it.
Just copy this in an empty file, rename it to something like apecue2flac, save it and make it executable by doing this:

```
chmod +x apecue2flac

```
Then you can copy it into /usr/bin, so it can be accesible anytime, anywhere:

```
sudo cp apecue2flac /usr/bin
```

Any comment welcome. (I apologize for my broken english).
It's been tested in Hardy and Intrepid.

This is it:
```

#!/bin/bash

clear

# Presentación

echo                              "APECUE2FLAC"
echo
echo
echo
echo "Script para convertir archivos ape con hoja cue asociada en archivos flac sueltos"
echo
echo
echo "ATENCIÓN: ESTE SCRIPT INSTALARÁ AUTOMÁTICAMENTE ALGUNOS DE LOS PAQUETES NECESARIOS PARA EJECUTARSE SI NO ESTÁN YA INSTALADOS."
echo
echo
echo
echo

# Comprueba si se tienen todas las herramientas necesarias y las instala si es necesario

MAC=`which mac`
if [ -z $MAC ]; then
echo "ERROR :-("
echo "No tienes instalado Monkey's Audio Codec."
echo "Busca en Google, que hay mucha información (Es fácil de instalar, pero no está en los repositorios). Te sugiero 
que añadas los repositorios de Eudoxos ([http://ppa.launchpad.net/eudoxos/ubuntu](http://ppa.launchpad.net/eudoxos/ubuntu) tuversióndeubuntu main), o que 
descargues el deb de aquí: http://members.iinet.net.au/~aidanjm/mac-3.99-u4_b3-1_i386.deb"
exit -1
fi

FLAC=`which flac`
if [ -z $FLAC ]; then
echo "ERROR SUBSANABLE ;-)"
echo "No tienes instalado flac, instalando automáticamente..."
sudo aptitude update && sudo aptitude install flac -y
clear
echo "ERROR CORREGIDO, CONTINUANDO..."
echo
fi

CUE=`which cuebreakpoints`
if [ -z $CUE ]; then
echo "ERROR SUBSANABLE ;-)"
echo
echo "No tienes instalado cuetools, instalando automáticamente..."
sudo aptitude update && sudo aptitude install cuetools -y
clear
echo "ERROR CORREGIDO, CONTINUANDO..."
echo
fi

SHN=`which shntool`
if [ -z $SHN ]; then
echo "ERROR SUBSANABLE ;-)"
echo
echo "No tienes instalado shntool, instalando automáticamente..."
sudo aptitude update && sudo aptitude install shntool -y
clear
echo "ERROR CORREGIDO, CONTINUANDO..."
echo
fi

LL=`which lltag`
if [ -z $LL ]; then
echo "ERROR SUBSANABLE ;-)"
echo
echo "No tienes instalado lltag, instalando automáticamente..."
sudo aptitude update && sudo aptitude install lltag -y
clear
echo "ERROR CORREGIDO, CONTINUANDO..."
echo
fi

# Verifica que hemos elegido un archivo cue y sale si no es así

for i in $*; do
case $i in
*.[cU][uU][eE])
echo "Verificando que el archivo $i tiene extensión cue...";;
*)
echo "Advertencia: El archivo $i no tiene extensión .cue. Abortando."
continue
esac

FILENAME="$(basename $i)"
FILENAME="${FILENAME%.[cC][uU][eE]}"

# Procesa los archivos

echo "Separando archivos..."
cuebreakpoints  $FILENAME.cue
shnsplit -o flac -f $FILENAME.cue $FILENAME.ape

echo "Añadiendo información de etiqueta..."
cuetag $FILENAME.cue split-track*.flac
echo

# Ahora renombra los archivos según el esquema "número de canción título", pero se puede cambiar como queramos,
# usando los comodines habituales. Consultar el manual de lltag para más información.

echo "Renombrando los archivos..."
lltag --yes --no-tagging --rename '%n %t' `ls split-track*.flac`
echo
echo
echo "Proceso terminado."
done
```

Now, this is the english version, as requested by nafihsus.
My english is not so good, but I think it can be understood, please, feel free to correct it and let me know the changes you might thing desirable: Thank you.
```
#!/bin/bash

clear

# Introduction

echo                              "APECUE2FLAC"
echo
echo
echo
echo "This bash script will convert and split ape files with associated cue files"
echo
echo
echo "WARNING: THIS SCRIPT WILL INSTALL NECESSARY PACKAGES IF NOT ALREADY INSTALLED"
echo
echo
echo
echo

# This will check your system for dependencies, and install packages if needed

MAC=`which mac`
if [ -z $MAC ]; then
echo "ERROR :-("
echo "Monkey's Audio Codec is not in your system"
echo "Do a Google search (it's easy to install, but it's not in the repositories). I suggest you to add the Eudoxos repositories (http://ppa.launchpad.net/eudoxos/ubuntu yourubuntuversion main), or you may prefer to download this deb: http://members.iinet.net.au/~aidanjm/mac-3.99-u4_b3-1_i386.deb"
exit -1
fi

FLAC=`which flac`
if [ -z $FLAC ]; then
echo "ERROR (Don't worry) ;-)"
echo "flac not found, automatically installing"
sudo aptitude update && sudo aptitude install flac -y
clear
echo "EVERYTHING OK, PROCEEDING..."
echo
fi

CUE=`which cuebreakpoints`
if [ -z $CUE ]; then
echo "ERROR (Don't worry) ;-)"
echo
echo "cuetools not found, automatically installing..."
sudo aptitude update && sudo aptitude install cuetools -y
clear
echo "EVERYTHING OK, PROCEEDING..."
echo
fi

SHN=`which shntool`
if [ -z $SHN ]; then
echo "ERROR (Don't worry) ;-)"
echo
echo "shntool not found, automatically installing..."
sudo aptitude update && sudo aptitude install shntool -y
clear
echo "EVERYTHING OK, PROCEEDING..."
echo
fi

LL=`which lltag`
if [ -z $LL ]; then
echo "ERROR (Don't worry) ;-)"
echo
echo "lltag not found, automatically installing..."
sudo aptitude update && sudo aptitude install lltag -y
clear
echo "EVERYTHING OK, PROCEEDING..."
echo
fi

# The following will verify if we have chosen a cue file, and exits if not

for i in $*; do
case $i in
*.[cU][uU][eE])
echo "Verifying file $i has a cue extension...";;
*)
echo "Warning: file $i is not a cue file. Aborting."
continue
esac

FILENAME="$(basename $i)"
FILENAME="${FILENAME%.[cC][uU][eE]}"

# Processes files

echo "Splitting files..."
cuebreakpoints  $FILENAME.cue
shnsplit -o flac -f $FILENAME.cue $FILENAME.ape

echo "Adding tags..."
cuetag $FILENAME.cue split-track*.flac
echo

# Now it renames files this way: "song-number title", but this can be changed as liked,
# using common parameters. Please read lltag manual for more information.

echo "Renaming files..."
lltag --yes --no-tagging --rename '%n %t' `ls split-track*.flac`
echo
echo
echo "End."
done
```

P. S.: I have posted a similar script that does the same with FLAC + CUE files [here]("http://ubuntuforums.org/showthread.php?t=1084840&highlight").

---

### Post by nafihsus on 2009-04-04
:p Hi txust, this is exactly what I was looking for. So far I always use the aidanjm [http://aidanjm.wordpress.com/]("http://aidanjm.wordpress.com/") tools manually. 
I run Hardy on a Dell PC and do convert quite some ape files which need renaming after splitting. What does your script expect as input parameters?

I definitely would be interested in an English version.

---

### Post by txust on 2009-04-04
Hi!
It renames the songs like this: "number title", with no dash or anything in between, but you can change it if you use other parameters instead of "%n %t". You can refer to the lltag manual. Hope it works for you. I will translate it.

---

### Post by nafihsus on 2009-04-04
Running the script without parameters resulted in downloading lots of modules the first time. However, the ape file in the directory is not being converted or split.
I receive a message:

ATENCIÓN: ESTE SCRIPT INSTALARÁ AUTOMÁTICAMENTE ALGUNOS DE LOS PAQUETES NECESARIOS PARA EJECUTARSE SI NO ESTÁN
YA INSTALADOS

But other than that nothing happens.

---

### Post by txust on 2009-04-04
Ok, now I understand, sorry. This script is intended to convert ape files which have a cue file associated. For example, you have an ape file 1.ape and its cue file is 1.cue.
if you run:
```
apecue2flac 1.cue
```
the script will split 1.ape into several flac files, tag and rename them using the information the cue file provides. So, it won't work with already splitted flac files. Try it with the original ape and cue file.
Let me know any other issue, and it's obvious I must translate it.

---

### Post by nafihsus on 2009-04-04
):P Thanks a lot. Script works perfect on my system. After my vacation I am going to try the cueflac2flac script.

---

### Post by TimCastle on 2009-04-06
Thank you txust.

I have .ape & .cues in hundreds of folders.

Can your script be changed to recursively convert and split files in a directory?

Can your script be changed to delete the original .ape files?

Can your script be changed to ignore .flac &.cues?

---

### Post by txust on 2009-04-06
Hello, TimCastle.
I'm not sure you can use this script recursively, and I don't think it's a good idea, because I have found that many cue files have to be edited before using apecue2flac, so using it recursively wouldn't work properly.
You can modify the script to delete the original ape files just by adding this line before it finishes:
```
rm *.ape
```
is that simple, but I wouldn't do that because if the cue file is not correct, the script would delete the ape anyway, leaving you with a cue file and no sound file. I suggest you to delete the ape files manually after conversion.
The script already ignores FLAC files, only works with files with ape extension. I have written another script to split, tag and rename FLAC + cue files, it's here:

[http://ubuntuforums.org/showthread.php?t=1084840&highlight](http://ubuntuforums.org/showthread.php?t=1084840&highlight)

(its name is flaccue2flac)

---

### Post by TimCastle on 2009-04-06
txust! Thank you very much for the detailed reply! 

As of now there is no way to convert a batche of .ape & .cues to individual .flac tracks while preserving the tag information. 

I will split all my .ape & .cues into .apes using 

[http://aidanjm.wordpress.com/2007/02/15/split-lossless-audio-ape-flac-wv-wav-by-cue-file/](http://aidanjm.wordpress.com/2007/02/15/split-lossless-audio-ape-flac-wv-wav-by-cue-file/)

And then run this script 

[http://legroom.net/software/convtoflac](http://legroom.net/software/convtoflac)

This appears to be the best choice for anyone in my situation.

---

### Post by txust on 2009-04-06
Hi!
My script does it, it converts ape + cue in splitted flac while preserves the tags. Its limitation is that it can't do it recursively, but those you have just posted neither do it, so it's better for you to use apecue2flac, give it a try.

---

### Post by DocForbin on 2009-05-02
Thanks for the script, very helpful. Note that it doesn't seem to work with filenames containing spaces.

---

### Post by dannymichel on 2009-08-28
anyone find a good gui cue splitter?

---

### Post by jamesisin on 2009-11-19
Hola.  Useful script.

What can you tell me about this Eudoxos repository you recommend?  I don't know anything about it.  It's on Launchpad so it's probably safe, but I'd like to know more nonetheless.

Also, do they have a key so I can secure the repository?

I notice that you are using cuebreakpoints in your script.  I don't believe that is necessary any longer.  Have a look at my post on splitting and tagging FLAC files:

[http://www.soundunreason.com/InkWell/?p=980](http://www.soundunreason.com/InkWell/?p=980)

This method (sans cuebreakpoints) seems to work perfectly for me.

I intend to write a post for APE files once I find a key and get some other small things sorted out.

---

### Post by txust on 2009-11-19
First of all, thanks for your feedback, I thought this script wasn't being used at all!

I really don't know anything about that repository, except that it works. It doesn't need a key, I have just installed this script in my system (8.04) and it didn't ask for a key, so... If you don't trust it, you can install the deb file from here:
[http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/]("http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/")
I didn't post this URL because I don't know if mac will stay there forever, that's why I said "look for it in Google", or something, but it's still there, I will edit my first post.
I'll give a try to your version without cuebreakpoints, and if it works I will change apecue2flac, although it works perfectly right now.
Thank you very much again!

---

### Post by jamesisin on 2009-12-08
Ok, I threw together an APE specific post:

[http://www.soundunreason.com/InkWell/?p=1282](http://www.soundunreason.com/InkWell/?p=1282)

Let me know if you see any troubles.

I did run into an APE file that when I try to split it, my entire system freezes (can't even ping or ssh into it).  Damn.  I'll have to try re-downloading it unless you happen to have any input on that one.

---

### Post by hgbso on 2009-12-17
I found an encoder that worked for me

I used 
the monkey audio tool with wine
[http://www.monkeysaudio.com/](http://www.monkeysaudio.com/)

to decompress to wav

then loaded the cue+wav into this encoder
[http://www.mediacoderhq.com/audio/](http://www.mediacoderhq.com/audio/)

it split the wav perfectly into individual flac

---

### Post by rene8 on 2010-01-14
Thanks all for all your posts. I wanted to do the same thing, and this thread helped me to actually write my own sript ;) .

I used many ideas from previous posts, but my script is rather simpler, in the sense that it assumes you have everything you need. It also does not use the MAC (Monkey's Audio Codec); instead of adding an 'unknown' repo, I decided to 'go the long way' and convert the .ape to .flac before splitting, using soundconverter.

I post next my own sript, for it might be of use to those that (like me) try to avoid adding 'unknown' repos.

FIRST: make sure you have soundconverter, shntool & cuetools packages installed.

NOTE: in honor to previous posts, I also named it apecue2flac ;) .

Here's the script:
```

#
# SCRIPT TO SPLIT A .ape FILE INTO .flac TRACKS USING .cue FILES
# Usage: apecue2flac APEfile.ape CUEfile.cue\n"
#
echo -e "SCRIPT TO SPLIT A .ape FILE INTO .flac TRACKS USING .ape.cue FILES\n"
echo -e "Usage: apecue2flac APEfile.ape CUEfile.cue\n"
#
echo "About to convert .ape into .flac ..."
soundconverter -b -m audio/x-flac -s .ape.flac "$1"
echo "About to split .flac into .flac tracks ..."
shnsplit -o flac -f "$2" -t "%n - %t" "$1.flac"
echo "Renaming spurious .flac files ..."
mv "$1.flac" "$1.flac.remove"
mv '00 - pregap.flac' '00 - pregap.flac.remove'
echo "Tagging flac files using .cue file ..."
cuetag "$2" *flac
echo "Cleaning up..."
rm *remove

```

Cheers to all!

*Footnote: I encourage everyone to try to avoid using windows tools with wine before looking for a way to do things in Ubuntu (or any distro)... I mean, we are working with Linux for a reason, right? hehe ;) .

---

### Post by arito on 2010-01-14
Thanks a bunch txust for the script. It worked well. I whish I had come here first, instead of spending 3 hours elsewhere without getting my file converted. It would be great if you could add a little more detailed advice to your first post for newbies (the instruction is pretty good already), so that using the script would be even more easy for them (hint: ask someone who's not computer savy to use your instruction under your observation to see what's difficult and what's not).

Thanks again :-)

---

### Post by marius_siuram on 2010-02-15
There are people (like me, with an amd64) that can't find any version of MAC that successfully works well in ubuntu.

Well there is a workaround... I found myself that wine works perfectly well (at least for me) with the proprietary executable on the Monkey's Audio Codec's official web. Converting it to wav and then reconverting is a ugly solution, but hey, it finally Worked For Me(TM)

To all those users that keep using the ape format: please please PLEASE Stop using it. Thanks ;)
I try to get rid of it as quickly as I can, but to do so I need to convert first xD

---

### Post by Bitter Peace on 2010-03-05
Thank you txust, this is a really useful script! Your work is much appreciated.

> **marius_siuram said:**
> To all those users that keep using the ape format: please please PLEASE Stop using it. Thanks ;)

Definitely this.

---

### Post by cascade9 on 2010-03-05
> **dannymichel said:**
> anyone find a good gui cue splitter?

I know, a couple of months late, but anyway- 

gcue2tracks-

[http://www.gtk-apps.org/content/show.php/gCue2tracks?content=80703](http://www.gtk-apps.org/content/show.php/gCue2tracks?content=80703)

> **marius_siuram said:**
> To all those users that keep using the ape format: please please PLEASE Stop using it. Thanks ;)

+2. Annoying format. It could be worse, I spose *cough* wma lossless *cough*

---

### Post by realoperadeal on 2010-03-26
Is there and idiots guide to this software - i'm about to throw my computer. just kidding - i love ubuntu, i am just not very good at it......

---

### Post by rene8 on 2010-03-26
> **realoperadeal said:**
> Is there and idiots guide to this software - i'm about to throw my computer. just kidding - i love ubuntu, i am just not very good at it......

And, what exactly is that you need help with? 
Can we help you?

---

### Post by realoperadeal on 2010-03-26
My computer freezes every time I try to fill in the fields so either I'm filling it in incorrectly or my ape/cue file is causing a crash.

Am I using it incorrectly?

---

### Post by jamesisin on 2010-03-26
realoperadeal - You can try using my blog post which goes through converting and tagging APE's to FLAC's:

[http://www.soundunreason.com/InkWell/?p=1282](http://www.soundunreason.com/InkWell/?p=1282)

---

### Post by realoperadeal on 2010-03-27
jamesisin,

your post is almost idiot proof enough for me, but not quite... when i put in the command (with replaced " marks and with the correct file names) it tells me that the files do not exist. 

everything I've done with ubuntu so far has been so easy, but this is making me crazy - thanks for helping me out!

---

### Post by rene8 on 2010-03-27
> **realoperadeal said:**
> jamesisin,
(with replaced " marks and with the correct file names) it tells me that the files do not exist. 


Keep the " marks as they are.
If you have a filename that contains special characters (such as a blank space) you'll need to write it within " or ' marks.

---

### Post by realoperadeal on 2010-03-27
For some reason it's still not working. i have moved the files to several locations and renamed them to a.ape and a.cue for simplicity. however, they are still are not being found. I've tried several different commands and they all come up with something like this:

shnsplit: warning: cannot open non-existent file: [a.ape]
shnsplit: error: cannot continue due to error(s) shown above
a.cue: error opening file
cuebreakpoints: error: unable to parse input file "a.cue"

any ideas?

thanks in advance!

---

### Post by realoperadeal on 2010-03-27
Strangely it is now working just fine! I must have been doing something wrong. Thanks for your help.

---

### Post by jamesisin on 2010-03-27
realoperadeal - As to the quotation marks, you can copy out of the code box instead of the other part of the post and you won't have to substitute them.  Either way, copy and paste the command line and its output into a code box here:

[NOPARSE]```
Paste the stuff between code brackets like this in your next post and it will appear in a code box.
```[/NOPARSE]

Also, could you include the outputs of pwd and ls -l so I can check your commands compared with your location.

You can do that either here or on my blog post.

---

### Post by rene8 on 2010-03-28
> **realoperadeal said:**
> Strangely it is now working just fine! I must have been doing something wrong. Thanks for your help.

Great! Glad to help ;)

---

### Post by Felipe. on 2010-09-25
> **marius_siuram said:**
> There are people (like me, with an amd64) that can't find any version of MAC that successfully works well in ubuntu.

Well there is a workaround... I found myself that wine works perfectly well (at least for me) with the proprietary executable on the Monkey's Audio Codec's official web. Converting it to wav and then reconverting is a ugly solution, but hey, it finally Worked For Me(TM)

To all those users that keep using the ape format: please please PLEASE Stop using it. Thanks ;)
I try to get rid of it as quickly as I can, but to do so I need to convert first xD

The solution to the amd64 lack of MAC versions:

&#8220;Here are newer and patched (some fixes) deb binaries (amd64 and i386) for mac: [https://launchpad.net/~g-christ/+archive/ppa](https://launchpad.net/~g-christ/+archive/ppa)  &#8221;

Someone has pointed it out in the following page: [http://www.webupd8.org/2009/04/split-ape-and-flac-files-in-ubuntu-and.html](http://www.webupd8.org/2009/04/split-ape-and-flac-files-in-ubuntu-and.html)

Direct link to MAC for amd64 .deb file: 

[https://launchpad.net/~g-christ/+archive/ppa/+build/1938504/+files/mac_3.99-u4-b5-s7-1~ppa1_amd64.deb](https://launchpad.net/~g-christ/+archive/ppa/+build/1938504/+files/mac_3.99-u4-b5-s7-1~ppa1_amd64.deb)

---

### Post by jamesisin on 2010-10-05
For those interested I have written a conversion script for APE/FLAC album length files:

[http://www.soundunreason.com/InkWell/?p=2485](http://www.soundunreason.com/InkWell/?p=2485)

---

### Post by jamesisin on 2011-02-22
Have you noticed any problems with the eudoxos repository?  I am trying to install MAC on a 10.04 machine and it's not working (I also tried it on a 9.10 with the same results).

---

### Post by jamesisin on 2011-02-24
It appears that the eudoxos repository no longer includes the MAC.  I was able to locate monkeys-audio by (cheating) using a different version's repository (I used intrepid instead of lucid).

I'd like information about a current repository for MAC if anyone can help.

---

### Post by cyanidin on 2011-08-21
> **txust said:**
> Hi everyone. I only registered to post this script, for I couldn't find anything that does this.
I'm spanish, so this script is in spanish too, but it's easy to understand, I think.
It basically converts an APE + CUE file in several FLAC files and  renames and tags them using the information provided by the cue sheet.  It also installs any package needed, except mac-port, but tells you how  to do it.
Just copy this in an empty file, rename it to something like apecue2flac, save it and make it executable by doing this:

```
chmod +x apecue2flac

```Then you can copy it into /usr/bin, so it can be accesible anytime, anywhere:

```
sudo cp apecue2flac /usr/bin
```Any comment welcome. (I apologize for my broken english).
It's been tested in Hardy and Intrepid.

This is it:
```

#!/bin/bash

clear

# Presentación

echo                              "APECUE2FLAC"
echo
echo
echo
echo "Script para convertir archivos ape con hoja cue asociada en archivos flac sueltos"
echo
echo
echo "ATENCIÓN: ESTE SCRIPT INSTALARÁ AUTOMÁTICAMENTE ALGUNOS DE LOS  PAQUETES NECESARIOS PARA EJECUTARSE SI NO ESTÁN YA INSTALADOS."
echo
echo
echo
echo

# Comprueba si se tienen todas las herramientas necesarias y las instala si es necesario

MAC=`which mac`
if [ -z $MAC ]; then
echo "ERROR :-("
echo "No tienes instalado Monkey's Audio Codec."
echo "Busca en Google, que hay mucha información (Es fácil de instalar, pero no está en los repositorios). Te sugiero 
que añadas los repositorios de Eudoxos ([http://ppa.launchpad.net/eudoxos/ubuntu](http://ppa.launchpad.net/eudoxos/ubuntu) tuversióndeubuntu main), o que 
descargues el deb de aquí: http://members.iinet.net.au/~aidanjm/mac-3.99-u4_b3-1_i386.deb"
exit -1
fi

FLAC=`which flac`
if [ -z $FLAC ]; then
echo "ERROR SUBSANABLE ;-)"
echo "No tienes instalado flac, instalando automáticamente..."
sudo aptitude update && sudo aptitude install flac -y
clear
echo "ERROR CORREGIDO, CONTINUANDO..."
echo
fi

CUE=`which cuebreakpoints`
if [ -z $CUE ]; then
echo "ERROR SUBSANABLE ;-)"
echo
echo "No tienes instalado cuetools, instalando automáticamente..."
sudo aptitude update && sudo aptitude install cuetools -y
clear
echo "ERROR CORREGIDO, CONTINUANDO..."
echo
fi

SHN=`which shntool`
if [ -z $SHN ]; then
echo "ERROR SUBSANABLE ;-)"
echo
echo "No tienes instalado shntool, instalando automáticamente..."
sudo aptitude update && sudo aptitude install shntool -y
clear
echo "ERROR CORREGIDO, CONTINUANDO..."
echo
fi

LL=`which lltag`
if [ -z $LL ]; then
echo "ERROR SUBSANABLE ;-)"
echo
echo "No tienes instalado lltag, instalando automáticamente..."
sudo aptitude update && sudo aptitude install lltag -y
clear
echo "ERROR CORREGIDO, CONTINUANDO..."
echo
fi

# Verifica que hemos elegido un archivo cue y sale si no es así

for i in "$*"; do
case $i in
*.[cU][uU][eE])
echo "Verificando que el archivo $i tiene extensión cue...";;
*)
echo "Advertencia: El archivo $i no tiene extensión .cue. Abortando."
continue
esac

FILENAME="$(basename "$i")"
FILENAME="${FILENAME%.[cC][uU][eE]}"

# Procesa los archivos

echo "Separando archivos..."
cuebreakpoints  "$FILENAME".cue
shnsplit -o flac -f "$FILENAME".cue "$FILENAME".ape

echo "Añadiendo información de etiqueta..."
cuetag "$FILENAME".cue split-track*.flac
echo

# Ahora renombra los archivos según el esquema "número de canción título", pero se puede cambiar como queramos,
# usando los comodines habituales. Consultar el manual de lltag para más información.

echo "Renombrando los archivos..."
lltag --yes --no-tagging --rename '%n %t' `ls split-track*.flac`
echo
echo
echo "Proceso terminado."
done
```Now, this is the english version, as requested by nafihsus.
My english is not so good, but I think it can be understood, please,  feel free to correct it and let me know the changes you might thing  desirable: Thank you.
```
#!/bin/bash

clear

# Introduction

echo                              "APECUE2FLAC"
echo
echo
echo
echo "This bash script will convert and split ape files with associated cue files"
echo
echo
echo "WARNING: THIS SCRIPT WILL INSTALL NECESSARY PACKAGES IF NOT ALREADY INSTALLED"
echo
echo
echo
echo

# This will check your system for dependencies, and install packages if needed

MAC=`which mac`
if [ -z $MAC ]; then
echo "ERROR :-("
echo "Monkey's Audio Codec is not in your system"
echo "Do a Google search (it's easy to install, but it's not in the  repositories). I suggest you to add the Eudoxos repositories  (http://ppa.launchpad.net/eudoxos/ubuntu yourubuntuversion main), or you  may prefer to download this deb:  http://members.iinet.net.au/~aidanjm/mac-3.99-u4_b3-1_i386.deb"
exit -1
fi

FLAC=`which flac`
if [ -z $FLAC ]; then
echo "ERROR (Don't worry) ;-)"
echo "flac not found, automatically installing"
sudo aptitude update && sudo aptitude install flac -y
clear
echo "EVERYTHING OK, PROCEEDING..."
echo
fi

CUE=`which cuebreakpoints`
if [ -z $CUE ]; then
echo "ERROR (Don't worry) ;-)"
echo
echo "cuetools not found, automatically installing..."
sudo aptitude update && sudo aptitude install cuetools -y
clear
echo "EVERYTHING OK, PROCEEDING..."
echo
fi

SHN=`which shntool`
if [ -z $SHN ]; then
echo "ERROR (Don't worry) ;-)"
echo
echo "shntool not found, automatically installing..."
sudo aptitude update && sudo aptitude install shntool -y
clear
echo "EVERYTHING OK, PROCEEDING..."
echo
fi

LL=`which lltag`
if [ -z $LL ]; then
echo "ERROR (Don't worry) ;-)"
echo
echo "lltag not found, automatically installing..."
sudo aptitude update && sudo aptitude install lltag -y
clear
echo "EVERYTHING OK, PROCEEDING..."
echo
fi

# The following will verify if we have chosen a cue file, and exits if not

for i in "$*"; do
case $i in
*.[cU][uU][eE])
echo "Verifying file $i has a cue extension...";;
*)
echo "Warning: file $i is not a cue file. Aborting."
continue
esac

FILENAME="$(basename $i)"
FILENAME="${FILENAME%.[cC][uU][eE]}"

# Processes files

echo "Splitting files..."
cuebreakpoints  "$FILENAME".cue
shnsplit -o flac -f "$FILENAME".cue "$FILENAME".ape

echo "Adding tags..."
cuetag "$FILENAME".cue split-track*.flac
echo

# Now it renames files this way: "song-number title", but this can be changed as liked,
# using common parameters. Please read lltag manual for more information.

echo "Renaming files..."
lltag --yes --no-tagging --rename '%n %t' `ls split-track*.flac`
echo
echo
echo "End."
done
```P. S.: I have posted a similar script that does the same with FLAC + CUE files [here]("http://ubuntuforums.org/showthread.php?t=1084840&highlight").

I modified the original script to fix a problem with filenames with  spaces. If the encoding of the file is not UTF-8, the characters will  not display properly. If you convert the format to UTF-8 with iconv  (depending on what the original encoding is), cuetag will work properly.

There is a more comprehensive tool available at [http://code.google.com/p/split2flac/](http://code.google.com/p/split2flac/)

---

