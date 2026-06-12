---
title: "Openshot does not start"
date: 2010-05-07
forum: Multimedia Software
---

### Post by tullo on 2010-05-07
Hello,
I'm trying to use Openshot video editor but it doesn't start, I have tried to uninstall all other video editor (kdenlive, cinelerra) cancel and re-install libraries (mlt, melt, ffmpeg...) but I always obtain this error:

giorgiatullo@family:~$ openshot
--------------------------------
    OpenShot (version 1.1.3)
--------------------------------
A new frmMain has been created
No formats or codecs were found.  Please check the OpenShot preferences 
and configure the 'melt' command name.
state saved
Segmentation fault
giorgiatullo@family:~$

I use ubuntu 10.04 but I had the same problem with 9.10 release, I have posted on the official Openshot forum but without result.
On my old computer that I gave to my daughter to play Hedgewars, with Ubuntu 10.04, Openshot works great... but is slow to use for video editing, maybe this could help me to understand my problem, but I don't know how.

This is openshot installation from console:

giorgiatullo@family:~$ sudo apt-get install openshot
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti saranno inoltre installati:
   libgoocanvas-common libgoocanvas3 libmlt++3 libmlt-data libmlt2 melt
   openshot-doc python-mlt2 python-pygoocanvas
I seguenti pacchetti NUOVI saranno installati:
   libgoocanvas-common libgoocanvas3 libmlt++3 libmlt-data libmlt2 melt
   openshot openshot-doc python-mlt2 python-pygoocanvas
0 aggiornati, 10 installati, 0 da rimuovere e 0 non aggiornati.
È necessario scaricare 0B/20,1MB di archivi.
Dopo quest'operazione, verranno occupati 39,7MB di spazio su disco.
Continuare [S/n]? s
Selezionato il pacchetto libgoocanvas-common.
(Lettura del database... 183570 file e directory attualmente installati.)
Estrazione di libgoocanvas-common (da 
.../libgoocanvas-common_0.15-0ubuntu2_all.deb)...
Selezionato il pacchetto libgoocanvas3.
Estrazione di libgoocanvas3 (da .../libgoocanvas3_0.15-0ubuntu2_i386.deb)...
Selezionato il pacchetto libmlt2.
Estrazione di libmlt2 (da .../libmlt2_0.5.4-1_i386.deb)...
Selezionato il pacchetto libmlt++3.
Estrazione di libmlt++3 (da .../libmlt++3_0.5.4-1_i386.deb)...
Selezionato il pacchetto libmlt-data.
Estrazione di libmlt-data (da .../libmlt-data_0.5.4-1_all.deb)...
Selezionato il pacchetto melt.
Estrazione di melt (da .../archives/melt_0.5.4-1_i386.deb)...
Selezionato il pacchetto python-mlt2.
Estrazione di python-mlt2 (da .../python-mlt2_0.5.4-1_i386.deb)...
Selezionato il pacchetto python-pygoocanvas.
Estrazione di python-pygoocanvas (da 
.../python-pygoocanvas_0.14.1-0ubuntu1_i386.deb)...
Selezionato il pacchetto openshot.
Estrazione di openshot (da .../openshot_1.1.3-1_all.deb)...
Selezionato il pacchetto openshot-doc.
Estrazione di openshot-doc (da .../openshot-doc_1.1.3-1_all.deb)...
Elaborazione dei trigger per man-db...
Elaborazione dei trigger per python-gmenu...
Rebuilding /usr/share/applications/desktop.it_IT.utf8.cache...
Elaborazione dei trigger per desktop-file-utils...
Elaborazione dei trigger per shared-mime-info...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Elaborazione dei trigger per python-support...
Configurazione di libgoocanvas-common (0.15-0ubuntu2)...
Configurazione di libgoocanvas3 (0.15-0ubuntu2)...

Configurazione di libmlt2 (0.5.4-1)...

Configurazione di libmlt++3 (0.5.4-1)...

Configurazione di libmlt-data (0.5.4-1)...
Configurazione di melt (0.5.4-1)...
Configurazione di python-mlt2 (0.5.4-1)...

Configurazione di python-pygoocanvas (0.14.1-0ubuntu1)...

Configurazione di openshot (1.1.3-1)...

Configurazione di openshot-doc (1.1.3-1)...

Elaborazione dei trigger per libc-bin...
ldconfig deferred processing now taking place
Elaborazione dei trigger per python-support...
giorgiatullo@family:~$


Thanks for your help.

Tullo

---

### Post by bcooperb on 2010-08-20
I have the same problem as far as trying to open Openshot, but nothing happens.


--------------------------------
   OpenShot (version 1.1.3)
--------------------------------
Process no longer exists: 4627.  Creating new pid lock file.
A new frmMain has been created
Segmentation fault


Anyone have any ideas?

---

### Post by domdeath on 2010-08-26
I have recently started having the same problem but its more annoying because it was working perfectly fine a week ago! I am half way through a project with a deadline of the start of october!

---

### Post by IceDoE on 2010-09-21
I have the same problem (saw your post over on the OpenShot forums too). This actually only started yesterday when I was fiddling around to try and get an updated version of 'melt' in 9.10 (the latest in the 9.10 repos is 0.4.4, in 10.04 it has 0.5.4).

I had been jumping through hoops to get the updated melt in order to fix the audio-sync issue in 0.4.4. It didn't like trying to update things and at some point, after installing a few packages to get melt to compile, it seemed to have both versions installed, and I couldn't unisntall the 0.4 version without uninstalling openshot. Somewhere around then it started giving me these errors.

Interestingly, in 9.10 when this happened I could still start openshot, it just popped up an error when I logged in telling me this info. In 10.04 it just flashes and closes.

Hope something in there helps. I've checked for all other dependencies and haven't found anything missing. Maybe something is wrong with melt? Maybe openshot doesn't know how to use the latest version of melt?

---

### Post by IceDoE on 2010-09-21
Got things working again!
Unfortunately this is not an ideal method, but I was suspicious:

I did a (mostly) clean reinstall of Ubuntu 10.04, then redid everything I had before (restricted extras, ubuntu studio packages, etc) and installed OpenShot using the ppa method on the openshotvideo site. 

Now it works again, though I haven't had much chance yet to see if if the audio sync has been corrected. Still, it seems to be using melt 5.4 now. 

I suspect now that the issue was in melt and in left over config files or something. I believe what was happening is Openshot was having trouble negotiating between two perceived versions of melt (the old 4.4 from 9.10 and the newer ones either personally compiled or from 10.04 repos).

I can only guess beyond that what you should do, but hopefully this helps anyone with more knowledge to figure out what to do as a proper fix.

---

### Post by IceDoE on 2010-12-20
Ok, after having this problem again in 10.10, I figured out how to fix it, and its a bit annoying:

First, just uninstall openshot (hopefully you saved your projects, of course). Uninstall melt and any other mlt packages you can find. Easy enough.

Now do a search for 'mlt', and remove/delete ALL the leftover mlt related files and packages. Be sure to ignore files that simply have a random mlt combination of letters in the name, but do go through and get every last one of those mlt files. I recommend also deleting the .openshot folder in your home directory just to be safe.

Now reinstall openshot.

Everything should work again.

---

### Post by KeesM on 2011-04-22
Unfortunately, removing melt/mlt files, removing .openshot etc and reinstalling openshot does not work for me, still segmentation fault... Anyone an idea?

```
kees@DualCore:/$ openshot
--------------------------------
   OpenShot (version 1.1.3)
--------------------------------
A new frmMain has been created
Segmentation fault
```

Thanks in advance...

---

### Post by KeesM on 2011-04-22
> **KeesM said:**
> Unfortunately, removing melt/mlt files, removing .openshot etc and reinstalling openshot does not work for me, ...

Looked somewhat further, the isse is not in melt, but in an apparently upgraded version of cairo (sneaked in through an upgraded version of GIMP)... Bug is known and in launchpad listed: [580130]("https://bugs.launchpad.net/openshot/+bug/580130").

The solution in short, do read the full thread (copied from launchpad from user [vagrale]("https://launchpad.net/~vagrale")):

[INDENT]i found a solution:
Open synaptic - find libcairo2 and chose it - press Ctrl+E - then choose ver 1.8.10
press coercion version and after choose Apply.
After that is ok!
look image [http://img638.imageshack.us/img638/6213/screenshotex.png](http://img638.imageshack.us/img638/6213/screenshotex.png)

After all just lock package libcairo2 version 1.8.10[/INDENT]

For me it worked! And GIMP still seems OK too. Now, how do I lock the package? Select package, go to Package menu, Lock Version.

---

### Post by Herbivore on 2012-10-10
> **IceDoE said:**
> Ok, after having this problem again in 10.10, I figured out how to fix it, and its a bit annoying:

First, just uninstall openshot (hopefully you saved your projects, of course). Uninstall melt and any other mlt packages you can find. Easy enough.

Now do a search for 'mlt', and remove/delete ALL the leftover mlt related files and packages. Be sure to ignore files that simply have a random mlt combination of letters in the name, but do go through and get every last one of those mlt files. I recommend also deleting the .openshot folder in your home directory just to be safe.

Now reinstall openshot.

Everything should work again.

IceDoE, here we are most of two years (20121010) after your post and this problem is still occuring. And your fix still works. 

OS: Linux Mint 13 (Ubuntu 12.04). 
Desktop environment: Cinnamon.

If you are listening, Thanks!

---

### Post by overdrank on 2012-10-10
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

