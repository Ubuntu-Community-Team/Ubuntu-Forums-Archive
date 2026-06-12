---
title: "Unable to install Octoshape"
date: 2008-09-20
forum: Multimedia Software
---

### Post by Xirtam on 2008-09-20
After downloading Octoshape from [http://superleagueformula.com/superleague/SF-Live/Online-broadcasting]("http://superleagueformula.com/superleague/SF-Live/Online-broadcasting") I follewed the instructions to install it.
Running the [COLOR="DarkRed"]chmod +x octosetup-linux_i386.bin[/COLOR]
and [COLOR="DarkRed"]./octosetup-linux_i386.bin[/COLOR] I get:


[COLOR="DarkRed"]Do you agree to these license terms? [yes|no]
yes
./octosetup-linux_i386.bin: 307: cannot create octoshape.installer.25635.25635: Permission denied
cat: octoshape.installer.25635.25635: No such file or directory
./octosetup-linux_i386.bin: 308: cannot create octoshape.installer.25635: Permission denied
unzip:  cannot find or open octoshape.installer.25635, octoshape.installer.25635.zip or octoshape.installer.25635.ZIP.
Go to octoshape and execute ./OctoshapeClient -url:octoshape:BROADCASTER.channel
rob@rob-laptop:/usr/src$ 
rob@rob-laptop:/usr/src$ [/COLOR]

What is going wrong here and what could be the sollution?

---

### Post by doug1212 on 2008-09-20
Hi,
There are some install instructions here:

[HTML]https://help.ubuntu.com/community/Octoshape[/HTML]

Doug.

---

### Post by Xirtam on 2008-09-20
Wauw, looks good. Will try it tomorrow and let you know.
Thanks in advance :-)

---

### Post by Xirtam on 2008-09-21
The installation went well. Also mplayer was installed and the java file that is needed.

To start all I used:
[COLOR="DarkRed"]```
./OctoshapeClient -url:octoshape:Superleague_formula
```[/COLOR]

Results:
[COLOR="DarkRed"]Status: Reading configuration
Status: Registering plugins.
Status: Ready to play
Status: Playing[/COLOR]

But no mplayer is started. :(

Later I used:
[COLOR="DarkRed"]```
./OctoshapeClient -url:Superleague_formula
```[/COLOR]

And that gave sound but no player was opened and no videostream was shown.

---

### Post by Xirtam on 2008-09-26
My setup.xml file:

```
<e JavaExec="/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/libjvm.so"
    TempID="Tju_Letden_Gunfe_08338370"/>

```

---

### Post by alexcckll on 2009-05-15
Personally I think it's mad that large broadcasters are sucking up end-users' bandwidth to serve up large video streams.  I am also not impressed with their insistence that they can autoupdate at any time...

Look - if they want to do that - do it the same way as Adobe have agreed - let the MOTU build a metapackage and let us host it centrally.

Better yet - I wish the EBU etc would get a clue and implement something more like iPlayer - a straight Flash client...

They can afford peering arrangements - end-users may be breaking their T&C by running p2p servers...

---

