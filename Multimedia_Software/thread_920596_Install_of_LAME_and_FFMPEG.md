---
title: "Install of LAME and FFMPEG"
date: 2008-09-15
forum: Multimedia Software
---

### Post by lemur1 on 2008-09-15
Hallo, 

I must install lame vor a video extention seyret (by joomla) by following the instructions from
[http://wiki.joomlaholic.com/index.php?title=Seyret#FLV_Conversion]("http://wiki.joomlaholic.com/index.php?title=Seyret#FLV_Conversion") 

Here is the beginning of it: 

> follow these steps: 

Prepare the directory structure 

```
mkdir am 
mkdir lib 
mkdir tmp 
chmod 777 tmp 
chmod 775 am 
chmod 775 lib 
```

Export some environment variables 

```
export TMPDIR=$HOME/tmp
export PATH=$HOME/bin:$PATH
export LD_LIBRARY_PATH=$HOME/lib:/usr/local/lib:$LD_LIBRARY_PATH
export CPATH=$HOME/include:/usr/local/include:$CPATH
export LIBRARY_PATH=$HOME/lib:/usr/local/lib:$LIBRARY_PATH
mkdir src
cd src

``` 


Install LAME 

```
wget http://nchc.dl.sourceforge.net/sourceforge/lame/lame-3.97.tar.gz
tar -zxvf lame-3.97.tar.gz
cd lame-3.97
./configure "--prefix=$HOME" "--enable-shared"
make
make install
```  

But by the command 
```
./configure "--prefix=$HOME" "--enable-shared"
```

I get the following: 

```
 ./configure "--prefix=$HOME" "--enable-shared" 
checking build system type... mkdir: cannot create directory `/root/tmp/cg14183-29935': No such file or directory 
mkdir: cannot create directory `/root/tmp/cg-14183': No such file or directory 
config.guess: cannot create a temporary directory in /root/tmp 
configure: error: cannot guess build type; you must specify one 
```

I assume, that it is the result of code (line 31667 - 31692 in ./configure):

```
# Have a temporary directory for convenience.  Make it in the build tree
# simply because there is no reason to put it here, and in addition,
# creating and moving files from /tmp can sometimes cause problems.
# Create a temporary directory, and hook for its removal unless debugging.
$debug ||
{
  trap 'exit_status=$?; rm -rf $tmp && exit $exit_status' 0
  trap '{ (exit 1); exit 1; }' 1 2 13 15
}
# Create a (secure) tmp directory for tmp files.
{
  tmp=`(umask 077 && mktemp -d -q "./confstatXXXXXX") 2>/dev/null` &&
  test -n "$tmp" && test -d "$tmp"
}  ||
{
  tmp=./confstat$$-$RANDOM
  (umask 077 && mkdir $tmp)
} ||
{
   echo "$me: cannot create a temporary directory in ." >&2
   { (exit 1); exit 1; }
}
_ACEOF
```

I have $HOME=/root

How can i overcome it, please?

Thanks

---

### Post by iponeverything on 2008-09-15
The snippet of variables export has a lot of spaces. get rid of them.

ie

export TMPDIR = $HOME/tmp 
export PATH = $HOME/bin:$PATH 
export LD_LIBRARY_PATH =$HOME/lib:/usr/local/lib:$LD_LIBRARY_PATH 
export CPATH = $HOME/include:/usr/local/include:$CPATH 
export LIBRARY_PATH = $HOME/lib:/usr/local/lib:$LIBRARY_PATH 
mkdir src 
cd src

from the error it does not like you did the "mkdir tmp"
step from the directory that you were working in.

---

### Post by lemur1 on 2008-09-16
Thank you for your reply.
But the spaces were my error only here on forum (in my post i have changed it just now).

And the problem with install stays yet. :(

---

### Post by mcduck on 2008-09-16
Both lame and ffmpeg are in repositories. Just install them with Ubuntu's package management and forget about compiling stuff.. ;)

---

### Post by lemur1 on 2008-09-16
> **mcduck said:**
> Both lame and ffmpeg are in repositories. Just install them with Ubuntu's package management and forget about compiling stuff.. ;)

Thank you, but, excuse me, i'm newbee :( :

I use ubuntu 6.06 ( on dedicated server).

I have made ```
#sudo apt-get install lame

```

Now i have lame at /usr/bin.

But the application doesn't work :(
./configure for my application need parameters:
```
./configure "--prefix=$HOME" "--enable-shared" "--enable-libmp3lame" "--extra-cflags=-I$HOME/include"  "--extra-ldflags=-L$HOME/lib"
```
"--prefix=$HOME" and $HOME=/root and so on.
(All instructions see in attachment file).

And I have 
```
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
 configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Jul 23 2008 21:50:24, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
```

What to do??

Thank you very much.

---

### Post by lemur1 on 2008-12-01
Excuse me, I repeat a post, but I need any solution really!
I have searched for it for a month :-((

---

### Post by mc4man on 2008-12-01
Edit :removed, irrelevant

---

### Post by lemur1 on 2008-12-02
[QUOTE=mc4man;6287772]Haven't looked at the configure options your using but Don't use the "...."  in your configure parameters.

Thank you,
I get the same result :-(

---

