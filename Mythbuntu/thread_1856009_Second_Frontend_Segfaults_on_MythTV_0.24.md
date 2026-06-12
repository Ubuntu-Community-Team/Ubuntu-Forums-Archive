---
title: "Second Frontend Segfaults on MythTV 0.24"
date: 2011-10-07
forum: Mythbuntu
---

### Post by jamoody on 2011-10-07
Mythfrontend segfaults when starting a second frontend via VNC, etc.   This is due to the a change where the frontend wants exclusive access to  the ServicePort.  Opening multiple mythfrontends can be achieved by  utilizing unique ~/.mythtv/config.xml files each with it's own  ServicePort, and then updating environment variable MYTHCONFDIR to point  to this unique configuration file.  

I modified /usr/share/mythtv/mythfrontend.sh to do this as follows:

...
#create a symbolic link for mysql.txt so it can't be overwritten
symlink

# jam - start multiple MythTV frontends

# ServicePort 6547 is the default so assume it's there and start with the next one
for ((a=6548; a<6557; a++));
do
  if !(ss -nl | grep $a >/dev/null);
     then break;
  fi
done

# point to correct .mythtv* directory based on first open port
b=$((a-6547))

#if ~/.mythtv? directory doesn't exist, create it and update config.xml with
#the port number
if [ ! -e ~/.mythtv$b/config.xml ]; then
#  mkdir ~/.mythtv$b/
#  cp ~/.mythtv/config.xml ~/.mythtv$b/
  cp -a ~/.mythtv ~/.mythtv$b
  sed -i.bak "s/<\/MythFrontend>/   <ServicePort>$a<\/ServicePort>\n     <\/MythFrontend>/g" ~/.mythtv$b/config.xml
fi

export MYTHCONFDIR=~/.mythtv$b
# jam - end


if [ "$1" = "--service" ]; then
    #source frontend session settings
...

Perhaps the owners of mythfrontend.sh (Mario Limonciello or  Michael Haas) would want to include some version of this code into mythfrontend.sh.  In the mean time you can manually paste this code (bounded by the "jam" tags) into /usr/share/mythtv/mythfrontend.sh to allow multiple mythfrontends via VNC.

---

### Post by nickrout on 2011-10-07
Why? what is the use of a frontend over vnc?

---

### Post by thatguruguy on 2011-10-07
I was going to respond to the OP, but I have no idea what he's talking about.

---

### Post by jamoody on 2011-10-09
I use multiple frontends via VNC on a non-zero display so I can setup/cleanup/check recordings, etc, either locally or remotely, without impacting the primary frontend (connected to the TV).  I'll often setup/review recordings while watching a recording, or do the same while at work without impacting whatever is being watched at home.

This ability has always existed in MythTV, but a recent fix has prevented it.  The suggested update to mythfrontend.sh restores that function.  Of course, one might argue that mythfrontend should never segfault and that should be the root cause investigation; the script update merely circumvents the segfault.

---

### Post by jamoody on 2011-10-09
BTW, I know I can also do these things via Mythweb, but I find a second, and sometimes a third, frontend to be much more convenient and efficient.  I can even validate the quality and completeness of a recording remotely by playing it in the VNC session (though I get no sound), which I don't believe I can do via Mythweb.  I've had trouble in the past with an STB not always changing channels correctly so by checking the recording from work I can restart it mid-recording (for a sporting event) or record a second showing later in the day (for a movie).

---

### Post by thatguruguy on 2011-10-09
I just used vnc to view my mythfrontend on my dedicated box, and had no issues.  I'm assuming this may be something unique to your own setup.

More importantly, I still don't understand the utility of what you're doing.  When I'm away from home, it seems that it is easier (and significantly more secure) to use mythweb than try to VNC into my mythbox over the internet. As far as other computers on the same network, is seems to make more sense to just install mythfrontend on those computers.

---

### Post by nickrout on 2011-10-09
> **jamoody said:**
> BTW, I know I can also do these things via Mythweb, but I find a second, and sometimes a third, frontend to be much more convenient and efficient.  I can even validate the quality and completeness of a recording remotely by playing it in the VNC session (though I get no sound), which I don't believe I can do via Mythweb.  I've had trouble in the past with an STB not always changing channels correctly so by checking the recording from work I can restart it mid-recording (for a sporting event) or record a second showing later in the day (for a movie).

you can do all that with mythweb.

---

### Post by jamoody on 2011-10-10
What version of MythTV are you using?  Early versions of 0.24 (0.24-2 and earlier) worked fine.  The problem started for me with 0.24-6.  

As I said, I know I can use mythweb, but I personally find a 2nd/3rd mythfrontend more convenient for remote recording management.  In any case, I don't believe mythfrontend shouldn't be segfaulting and this is a workaround to prevent that.  I can provide doc as needed (just let me know how to get it).  I know other users have seen this in Mythdora as well.  [http://www.mythdora.com/?q=node/5821](http://www.mythdora.com/?q=node/5821)

---

### Post by thatguruguy on 2011-10-10
> **jamoody said:**
> What version of MythTV are you using?  Early versions of 0.24 (0.24-2 and earlier) worked fine.  The problem started for me with 0.24-6.  

As I said, I know I can use mythweb, but I personally find a 2nd/3rd mythfrontend more convenient for remote recording management.  In any case, I don't believe mythfrontend shouldn't be segfaulting and this is a workaround to prevent that.  I can provide doc as needed (just let me know how to get it).  I know other users have seen this in Mythdora as well.  [http://www.mythdora.com/?q=node/5821](http://www.mythdora.com/?q=node/5821)

What is 0.24-6?  The current point release is 0.24.1.  The most recent version of .24 in the mythbuntu repository is .24.1+fixes.20111010

Are you using mythbuntu?  Again, are you certain this isn't just a problem on your particular setup?

---

### Post by nickrout on 2011-10-10
> **jamoody said:**
> What version of MythTV are you using?  Early versions of 0.24 (0.24-2 and earlier) worked fine.  The problem started for me with 0.24-6.  

As I said, I know I can use mythweb, but I personally find a 2nd/3rd mythfrontend more convenient for remote recording management.  In any case, I don't believe mythfrontend shouldn't be segfaulting and this is a workaround to prevent that.  I can provide doc as needed (just let me know how to get it).  I know other users have seen this in Mythdora as well.  [http://www.mythdora.com/?q=node/5821](http://www.mythdora.com/?q=node/5821)

So why aren't you using mythfrontend on the machine you want to use it on? why vnc? Just install mythfrontend wherever you want to use it.

---

### Post by jamoody on 2011-10-12
I am in the process of migrating from MythDora to Mythbuntu.  The same  problem occurs on MythDora and is being seen by others there as well.   See [http://www.mythdora.com/?q=node/5821;](http://www.mythdora.com/?q=node/5821;) the link to my solution is at  the bottom, including the underlying cause for the segfault (an invalid  argument on a mutex unlock).

I don't believe this is a problem with my particular setup.  To see the  problem you must have multiple mythfrontends up and activated from the  same userid; I doubt VNC in particular is necessary for the problem; I  would expect this to be re-creatable from the primary login being used  for playback.  I am currently running Mythbuntu v0.24.1-95 and the  problem persists there.

I often setup and check on recordings from work, a Windows machine that I  can't install MythTV on.  VNC is the solution I use to get around this.

If the owners of the code don't think this is a general enough problem  to warrant fixing, that's fine.  Just sharing the cause and workaround  for this problem may be enough for anyone else that's seeing it and finds this thread.

---

### Post by jamoody on 2011-10-12
.

---

### Post by nickrout on 2011-10-12
> **jamoody said:**
> I am in the process of migrating from MythDora to Mythbuntu.  The same  problem occurs on MythDora and is being seen by others there as well.   See [http://www.mythdora.com/?q=node/5821;](http://www.mythdora.com/?q=node/5821;) the link to my solution is at  the bottom, including the underlying cause for the segfault (an invalid  argument on a mutex unlock).

I don't believe this is a problem with my particular setup.  To see the  problem you must have multiple mythfrontends up and activated from the  same userid; I doubt VNC in particular is necessary for the problem; I  would expect this to be re-creatable from the primary login being used  for playback.  I am currently running Mythbuntu v0.24.1-95 and the  problem persists there.

I often setup and check on recordings from work, a Windows machine that I  can't install MythTV on.  VNC is the solution I use to get around this. mythweb?> 

If the owners of the code don't think this is a general enough problem  to warrant fixing, that's fine.  Just sharing the cause and workaround  for this problem may be enough for anyone else that's seeing it and finds this thread.
what makes you think any of the mythtv devs hangs about here? report a bug and it might get fixed!

---

