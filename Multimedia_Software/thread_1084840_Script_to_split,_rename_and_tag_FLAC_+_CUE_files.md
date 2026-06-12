---
title: "Script to split, rename and tag FLAC + CUE files"
date: 2009-03-02
forum: Multimedia Software
---

### Post by txust on 2009-03-02
I have just finished this new script based on the other I posted before. This one will split, rename and tag all those FLAC + cue files we usually found encoded with EAC. Use the same procedure I suggested in

[http://ubuntuforums.org/showthread.php?t=1084665&]("http://ubuntuforums.org/showthread.php?t=1084665&")

It's also in spanish, but it's very easy to understand. I can translate it on request.
It's been tested in Hardy and Intrepid.

Here it is:

```
#!/bin/bash

clear

# Presentación

echo
echo
echo                   "FLACCUE2FLAC"
echo
echo
echo
echo "Script para convertir archivos FLAC con hoja cue asociada en archivos FLAC sueltos"
echo
echo
echo "ATENCIÓN: ESTE SCRIPT INSTALARÁ AUTOMÁTICAMENTE ALGUNOS DE LOS PAQUETES NECESARIOS PARA EJECUTARSE SI NO ESTÁN 
YA INSTALADOS"
echo
echo
echo
echo

# Comprueba que están instalados los paquetes necesarios y los instala si no es así

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

# Verifica que hemos elegido un archivo cue

for i in $*; do
case $i in
*.[cU][uU][eE])
echo "Verificando si el archivo $i tiene extensión cue...";;
*)
echo "Advertencia: El archivo $i no tiene extensión .cue. Abortando."
continue
esac

# Procesa los archivos

FILENAME="$(basename $i)"
FILENAME="${FILENAME%.[cC][uU][eE]}"

echo "Separando archivos..."
cuebreakpoints  $FILENAME.cue
shnsplit -o flac -f $FILENAME.cue $FILENAME.flac

echo "Añadiendo información de etiqueta..."
cuetag $FILENAME.cue split-track*.flac

# Renombra los archivos siguiendo la estructura "número de pista título", que es la que uso, pero se puede
# modificar fácilmente usando los comodines habituales. Consultar el manual de lltag para más información.

echo "Renombrando archivos..."
lltag --yes --no-tagging --rename '%n %t' `ls split-track*.flac`
echo
echo
echo "Proceso terminado."
done
```

This is the english version, as requested by nafihsus

```
#!/bin/bash

clear

# Introduction

echo
echo
echo                   "FLACCUE2FLAC"
echo
echo
echo
echo "This script will convert, split and tag FLAC files with an associated cue sheet"
echo
echo
echo "WARNING: THIS SCRIPT WILL AUTOMATICALLY INSTALL SOME NECESSARY PACKAGES IF NOT ALREADY INSTALLED"
echo
echo
echo
echo

# This will check if all packages needed are present in the system, and will install them if not.

FLAC=`which flac`
if [ -z $FLAC ]; then
echo "ERROR (Don't worry) ;-)"
echo "FLAC is not in your system, automatically installing..."
sudo aptitude update && sudo aptitude install flac -y
clear
echo "OK NOW, PROCEEDING..."
echo
fi

CUE=`which cuebreakpoints`
if [ -z $CUE ]; then
echo "ERROR (Wish every error were like this one...) ;-)"
echo
echo "cuetools not present, automatically installing..."
sudo aptitude update && sudo aptitude install cuetools -y
clear
echo "OK NOW, PROCEEDING..."
echo
fi

SHN=`which shntool`
if [ -z $SHN ]; then
echo "ERROR (Not the end of the world, anyway) ;-)"
echo
echo "shntool is not around here, let's get it..."
sudo aptitude update && sudo aptitude install shntool -y
clear
echo "OK, PROCEEDING..."
echo
fi

LL=`which lltag`
if [ -z $LL ]; then
echo "OH, MY GOD! ;-)"
echo
echo "lltag is not in your computer, installing..."
sudo aptitude update && sudo aptitude install lltag -y
clear
echo "AT LAST, PROCEEDING..."
echo
fi

# Now it will check if we have chosen a cue file

for i in $*; do
case $i in
*.[cU][uU][eE])
echo "Checking if file $i is a .cue file...";;
*)
echo "Warning: File $i is not a .cue file. Aborting."
continue
esac

# Processing files

FILENAME="$(basename $i)"
FILENAME="${FILENAME%.[cC][uU][eE]}"

echo "Splitting files..."
cuebreakpoints  $FILENAME.cue
shnsplit -o flac -f $FILENAME.cue $FILENAME.flac

echo "Adding tags..."
cuetag $FILENAME.cue split-track*.flac

# This will rename files using the strucure "track-number title", the one I like, but it can be easyly changed using common parameters. Please read lltag manual for more information.

echo "Renaming files..."
lltag --yes --no-tagging --rename '%n %t' `ls split-track*.flac`
echo
echo
echo "Process ended."
done
```

---

### Post by nafihsus on 2009-06-06
Hi txust,

would you mind translating flaccue2flac also into English?

By the way, sometimes the apecue2flac script skips the first song in a cue file with a message like "too short" and then gets the sequence of the tags wrong (song no2 getting the tag of no 1 ...).

---

### Post by txust on 2009-06-07
> **nafihsus said:**
> Hi txust,

would you mind translating flaccue2flac also into English?

By the way, sometimes the apecue2flac script skips the first song in a cue file with a message like "too short" and then gets the sequence of the tags wrong (song no2 getting the tag of no 1 ...).

Ok, I will translate it, no problem.
That problem you have found is not a problem in the script, but in the cue file, you have to edit it. It has happened to me several times, but I don't remember how I edited the cue file to make it work properly, but it is not difficult. I think it was quite often an issue with cue files generated by the Windows program EAC. If you find the solution, please, post it here. Thank you.

---

### Post by nafihsus on 2009-06-13
These two formats seem to be ok:
 
TRACK 01 AUDIO
    TITLE "song 1"
    PERFORMER "Mr X"
    INDEX 01 00:00:00
  TRACK 02 AUDIO
    TITLE "song 2"
    PERFORMER "Mr X"
    INDEX 01 04:51:52
  TRACK 03 AUDIO
 
and so on or 

  TRACK 01 AUDIO
    TITLE "song 1"
    PERFORMER "Mrs Y"
    INDEX 01 00:00:00
  TRACK 02 AUDIO
    TITLE "song 2"
    PERFORMER "Mrs Y"
    INDEX 00 05:36:21
    INDEX 01 05:36:23
  TRACK 03 AUDIO

Not ok is following format:

  TRACK 01 AUDIO
    TITLE "song 1"
    PERFORMER "Group Z"
    INDEX 00 00:00:00
    INDEX 01 00:00:62
  TRACK 02 AUDIO
    TITLE "song 2"
    PERFORMER "Group Z"
    INDEX 00 07:06:55
    INDEX 01 07:08:22
  TRACK 03 AUDIO

However, if confirmed as correct than it should be posted somewhere else as no one would find the post in this thread.

---

### Post by txust on 2009-06-20
> **nafihsus said:**
> 
However, if confirmed as correct than it should be posted somewhere else as no one would find the post in this thread.

Ok, but where could it be posted?

---

### Post by bliffle on 2009-09-13
That's a great script - thanks for posting it.

Worked good on most files, but then choked on a FILE statement (in a cue file) that named a .flac and proclaimed it a WAV. I don't know what that means. I need a good description of cue file content. 

Since the cue and flac were generated by EAC I installed it (windows XP) and tried burning, but it failed.

---

### Post by djfraggle on 2010-02-14
Does anyone know all the fields cuetag will use? I've found that GENRE is acceptable, but DATE, YEAR & COMMENT throw up errors. Most of my cue's have year/date in them (REM'd out), so it'd be nice to tag these as well. Thanks!

---

### Post by graben3 on 2011-01-28
Big Thank You for this script.... this is exactly what I was searching for !

---

### Post by powerpleb on 2011-04-20
Gar! It won't work if there are spaces in the filename.

---

### Post by intel352 on 2011-06-02
Use Flacon instead, find it in Software Center, has GUI, works quite well.

---

