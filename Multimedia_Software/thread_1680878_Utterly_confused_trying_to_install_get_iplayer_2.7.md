---
title: "Utterly confused trying to install get_iplayer 2.79"
date: 2011-02-03
forum: Multimedia Software
---

### Post by XEtedBear on 2011-02-03
I wish to install the latest version of get_iplayer. The manual installation instructions at [http://linuxcentre.net/getiplayer/installation](http://linuxcentre.net/getiplayer/installation) are:
```

wget http://linuxcentre.net/get_iplayer/get_iplayer
chmod 755 get_iplayer

```
They do not work: I receive an error message if I enter the command 'get_iplayer' that tells me that get_iplayer is not installed.

Using the Linux deb package installation, rather than the manual installation, instructions at this same web site results in the  installation of version 2.78.

If I visit the recommended site for the latest version of get_iplayer, at 
[http://www.infradead.org/get_iplayer/html/get_iplayer.html](http://www.infradead.org/get_iplayer/html/get_iplayer.html), then I am directed to an ftp site from which I can download version 2.79. When I extract the contents of the downloaded archive file I find a README text file which immediately directs me back to the original Paul Lewis web-site and gives me no idea of how to install version 2.79.

It appears I am going round in circles.

Is it possible to install version 2.79 or am I misunderstanding it all? By the way, is the application called 'get-iplayer' or 'get_iplayer'?

---

### Post by AlecJ on 2011-02-03
Scroll down the screen and use the Ubuntu repository

wget [http://linuxcentre.net/get_iplayer/packages/get-iplayer-current.deb](http://linuxcentre.net/get_iplayer/packages/get-iplayer-current.deb)
sudo dpkg -i get-iplayer-current.deb
sudo apt-get -f install 


oh it's get-iplayer  then the string of what media and what type of file etc

---

### Post by howefield on 2011-02-03
> **XEtedBear said:**
> ```

wget http://linuxcentre.net/get_iplayer/get_iplayer
chmod 755 get_iplayer

```
They do not work: I receive an error message if I enter the command 'get_iplayer' that tells me that get_iplayer is not installed.

All you have done is download a file and change its permission, You haven't installed anything yet.

Open the downloaded file and look for a readme or install file.

Get the file from here...

[ftp://ftp.infradead.org/pub/get_iplayer/](ftp://ftp.infradead.org/pub/get_iplayer/)

---

### Post by nothingspecial on 2011-02-03
I don`t think the one in the repos works anymore due to something the bbc did.

Do this instead

```
wget ftp://ftp.infradead.org/pub/get_iplayer/get_iplayer-2.78.tar.gz
```
```

tar -xvf get_iplayer-2.78.tar.gz
```

Then to run it either 

```
cd get_iplayer-2.78
./get_iplayer -blah -blah
```

Or you can move it 

```
sudo mv get_iplayer-2.78/get_iplayer /usr/bin/
```

After you`ve done that you can run it from anywhere.

---

### Post by ajgreeny on 2011-02-03
I originally installed the repository version of 2.66 in my Lucid, but since then have simply been updating the perl script **get_iplayer**, in /usr/bin, by downloading the newest version from [ftp://ftp.infradead.org/pub/get_iplayer/](ftp://ftp.infradead.org/pub/get_iplayer/), unpacking it, and then backing up the old perl script in /usr/bin and replacing with the new one.

That is working brilliantly now; version 2.79

---

### Post by nothingspecial on 2011-02-03
Thanks for the heads up on 2.79, hadn`t noticed.

---

### Post by ajgreeny on 2011-02-03
Yet another update on the situation.

I have just found a deb package for natty which certainly works fine in Lucid, and being such a simple package may also work in older ubuntu versions as well.  You can get it from [https://launchpad.net/ubuntu/+source/get-iplayer/2.79-1/+buildjob/2157311](https://launchpad.net/ubuntu/+source/get-iplayer/2.79-1/+buildjob/2157311) then just double click on the .deb file and it will be installed.

Great!

---

### Post by shantiq on 2011-02-03
hi nothingspecial   did you mean 2.79 or 2.78 [earlier on]("http://ubuntuforums.org/showpost.php?p=10424231&postcount=4") because it works with 2.79 too


```
wget ftp://ftp.infradead.org/pub/get_iplayer/get_iplayer-2.79.tar.gz
```
Code:
```
tar -xvf get_iplayer-2.79.tar.gz

``` 



Code:
```
sudo mv get_iplayer-2.79/get_iplayer /usr/bin/
```

then to terminal    enter    ```
get_iplayer
``` or ```
get-iplayer
```

---

### Post by g1suh on 2011-02-03
There is a very simple way of installing get-iplayer. I am quite happy to use a shell to execute commands, but I'd rather use a mouse...
I've just installed get-iplayer on this machine and downloaded a BBC programme to prove it works. Method:

Install get-iplayer with synaptic - this will sort out dependencies.
If you go to this page: [http://packages.ubuntu.com/natty/get-iplayer](http://packages.ubuntu.com/natty/get-iplayer)

this will provide a newer version. Double click on the .deb file when you have downloaded it. You will be advised to use the older version - ignore this warning. Once this is installed (not forgetting to close synaptic before you double click) you will be able to download programmes.
 get-iplayer -h gives you instructions.

---

### Post by haydoni on 2011-05-07
Weird, get-iplayer doesn't show up in the Software Centre (I'm sure it used to in 10.10...) or the Dash. Works fine from Synaptic, 2.79.

---

### Post by tpprynn on 2011-06-04
Have people here found this has stopped working again? I've not been having much luck, in Ubuntu 10.04, Debian 6.01 and Mint 9, 10 and 11. It briefly stopped working in Windows but got going again with a new version of flvstreamer.

Currently using Ubuntu 10.04 32 bit and had installed the repository version and then updated get_iplayer to 2.79.1.

Mint 11's version worked for a radio programme but not tv. The fact that the Windows version works in Windows 7 suggests the problem is not BBC intervention.

I've several forms of the command for recording including:

get_iplayer --modes=flashstd --pid [then the url]

and a quick search:

get_iplayer --get [comedian's name]

then

get_iplayer --get 622

once the program has given me the code number of the show I searched for

Thanks for any tips. Odd this should  fail for me on three different machines and distros when some people seem to have it working.

---

### Post by ron999 on 2011-06-04
> **tpprynn said:**
> Have people here found this has stopped working again? 
...
Thanks for any tips.

Hi
get_iplayer's working fine.

With Ubuntu...

Use the very latest get_iplayer script from here:- [http://git.infradead.org/get_iplayer.git]("http://git.infradead.org/get_iplayer.git")
Download it:-
```
git clone git://git.infradead.org/get_iplayer.git
```

Install it:-
```
sudo cp ~/get_iplayer/get_iplayer /usr/bin/get_iplayer
```

And install RTMPDump.
```
sudo apt-get install rtmpdump
```

---

### Post by tpprynn on 2011-06-04
I get this at the first hurdle (and I have git-core installed):

lee@lee-netbook:/$ git clone git://git.infradead.org/get_iplayer.git
fatal: could not create work tree dir 'get_iplayer'.: Permission denied
lee@lee-netbook:/$

Which version of Ubuntu have you got? Thanks. This is driving me mad, it's a great and handy program...

---

### Post by ron999 on 2011-06-04
> **tpprynn said:**
> 
lee@lee-netbook:/$ git clone git://git.infradead.org/get_iplayer.git
fatal: could not create work tree dir 'get_iplayer'.: [COLOR="Red"]Permission denied[/COLOR]

Try to fix this.

> ron@ubuntu:~$ git clone git://git.infradead.org/get_iplayer.git
Initialized empty Git repository in /home/ron/get_iplayer/.git/
remote: Counting objects: 1797, done.
remote: Compressing objects: 100% (456/456), done.
remote: Total 1797 (delta 1319), reused 1797 (delta 1319)
Receiving objects: 100% (1797/1797), 1.14 MiB | 426 KiB/s, done.
Resolving deltas: 100% (1319/1319), done.


---

### Post by nothingspecial on 2011-06-04
> **tpprynn said:**
> 
lee@lee-netbook:/$



You are in your root folder, try typing ```
cd
``` and try again.

---

### Post by tpprynn on 2011-06-04
i'm thinking now actually that the trouble I've had is to do with Ubuntu Restricted Extras. I ran 11.04 from a stick, installed get_iplayer and successfully managed to get a download started from BBC2. So I installed 11.04 and added the Restricted stuff - now get_iplayer doesn't work again. Some codec clash somewhere. Maybe someone will have an idea.

---

### Post by shantiq on 2011-06-05
ttpryn


how about


simply using


```
sudo apt-get install get-iplayer
```   **but**   before you do that make sure you have all of the ones in the synaptic recommended dependencies ticked and installed **and** the 2 perl ones


maybe try that


what happens if you do that?   2.79 is the version on natty now

---

### Post by heyup on 2011-06-10
This message on the get_iplayer mailing list regarding Ubuntu packages may help:-

[http://lists.infradead.org/pipermail/get_iplayer/2011-June/001613.html](http://lists.infradead.org/pipermail/get_iplayer/2011-June/001613.html)

You need to read the mailing list to keep up to date.

[http://lists.infradead.org/pipermail/get_iplayer/](http://lists.infradead.org/pipermail/get_iplayer/)

---

### Post by jon47 on 2011-06-10
> **heyup said:**
> This message on the get_iplayer mailing list regarding Ubuntu packages may help:-

[http://lists.infradead.org/pipermail/get_iplayer/2011-June/001613.html](http://lists.infradead.org/pipermail/get_iplayer/2011-June/001613.html)

You need to read the mailing list to keep up to date.

[http://lists.infradead.org/pipermail/get_iplayer/](http://lists.infradead.org/pipermail/get_iplayer/)

I was looking for something else and found this thread, but you've quoted me already ;-)

You need to either
(a) use the version packaged with your version of Ubuntu, which will mostly work, or
(b) use the ppa I put together which has recent versions of the dependencies, and works much better:

ppa:jon-hedgerows/get-iplayer

Cheers
Jon

---

### Post by Windcheetah on 2012-01-18
> **nothingspecial said:**
> I don`t think the one in the repos works anymore due to something the bbc did.

Do this instead

```
wget ftp://ftp.infradead.org/pub/get_iplayer/get_iplayer-2.78.tar.gz
``````

tar -xvf get_iplayer-2.78.tar.gz
```Then to run it either 

```
cd get_iplayer-2.78
./get_iplayer -blah -blah
```Or you can move it 

```
sudo mv get_iplayer-2.78/get_iplayer /usr/bin/
```After you`ve done that you can run it from anywhere.

I've just done all than and I get:

"martin@martin-desktop:~/Downloads/get_iplayer-2.80$ ./get_iplayer
Can't locate HTML/Entities.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at ./get_iplayer line 59.
BEGIN failed--compilation aborted at ./get_iplayer line 59.
martin@martin-desktop:~/Downloads/get_iplayer-2.80$"

Can anyone see where I've gone wrong??? As you can see, I'm using 2.80, if that makes any difference
Martin

---

### Post by jon47 on 2012-01-19
> **Windcheetah said:**
> I've just done all than and I get:

"martin@martin-desktop:~/Downloads/get_iplayer-2.80$ ./get_iplayer
Can't locate HTML/Entities.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at ./get_iplayer line 59.
BEGIN failed--compilation aborted at ./get_iplayer line 59.
martin@martin-desktop:~/Downloads/get_iplayer-2.80$"

Can anyone see where I've gone wrong??? As you can see, I'm using 2.80, if that makes any difference
Martin

You don't have all the required perl modules installed.  Note also that how well get_iplayer works is critically dependent on both ffmpeg and rtmpdump (or flvstreamer) - so even if you fix this, you still need a relatively recent build of these other applications.

In short, what you need to do is:

$ sudo add-apt-repository ppa:jon-hedgerows/get-iplayer
$ sudo apt-get update
$ sudo apt-get install get-iplayer

and it will work fine.  Incidentally there are known bugs in v2.80, but not enough to have yet produced a 2.81.  This repository tracks bug-fixed versions and so is typically a few revisions ahead of the latest released version.

Active support for get-iplayer is available on the get-iplayer mailing list which you can subscribe to here: [http://lists.infradead.org/mailman/listinfo/get_iplayer](http://lists.infradead.org/mailman/listinfo/get_iplayer)

Cheers
Jon

---

