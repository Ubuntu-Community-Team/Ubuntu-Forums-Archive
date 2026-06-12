---
title: "No Apple Trailer Plugin and control-center has python error"
date: 2008-10-27
forum: Mythbuntu
---

### Post by Lindsay.Mathieson on 2008-10-27
Only noticed this recently

My real mythbuntu htpc and the desktop (test) one both work of weekly fixes. The desktop is Kubuntu 8.10RC

When I start mythbuntu-control-centre on the desktop there's a new plugin - "Apple Trailers" which works as advertised.

When I start mythbuntu-control-centre on the HTPC there no "Apple Trailers" and I get this error on the console:
```
sudo mythbuntu-control-centre Reading package lists... Done
Building dependency tree       
Reading state information... Done
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:208: GtkWarning: gtk_file_folder_unix_get_info: assertion `strcmp (dirname, folder_unix->filename) == 0' failed
  gtk.main()

```

I've reinstalled control centre with ```
sudo apt-get install --reinstall mythbuntu-control-centre
``` but that made no difference.

Any suggestions?

Thanks,

Lindsay

---

### Post by tgm4883 on 2008-10-27
> **Lindsay.Mathieson said:**
> Only noticed this recently

My real mythbuntu htpc and the desktop (test) one both work of weekly fixes. The desktop is Kubuntu 8.10RC

When I start mythbuntu-control-centre on the desktop there's a new plugin - "Apple Trailers" which works as advertised.

When I start mythbuntu-control-centre on the HTPC there no "Apple Trailers" and I get this error on the console:
```
sudo mythbuntu-control-centre Reading package lists... Done
Building dependency tree       
Reading state information... Done
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:208: GtkWarning: gtk_file_folder_unix_get_info: assertion `strcmp (dirname, folder_unix->filename) == 0' failed
  gtk.main()

```

I've reinstalled control centre with ```
sudo apt-get install --reinstall mythbuntu-control-centre
``` but that made no difference.

Any suggestions?

Thanks,

Lindsay

Not sure about the error, but the apple trailer plugin wasn't packaged yet in Hardy.

---

### Post by Lindsay.Mathieson on 2008-10-28
> **tgm4883 said:**
> Not sure about the error, but the apple trailer plugin wasn't packaged yet in Hardy.

Ah, that's probably it then, the desktop is cutting edge - Intrepid RC, I'm rather more conservative with the HTPC as that's what the wife uses :)

Thanks.

---

### Post by superm1 on 2008-10-28
So you tried to install the newer MCC on the older box then right?  Just want to make sure there isn't a bug in the newer MCC "in intrepid"

---

### Post by Lindsay.Mathieson on 2008-10-29
> **superm1 said:**
> So you tried to install the newer MCC on the older box then right?  Just want to make sure there isn't a bug in the newer MCC "in intrepid"

Sorry re the late reply ...

Not a hundred percent sure what you mean :) but I'll specify what I have.

HTPC Running Mythbuntu 8.04.1 + Weekly Fixes, no custom installs
 - No Apple Trailiers
 - Console shows "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:208" etc wehn starting MCC

Destop PC running Kubuntu 8.10RC
  - MythTV installed vi Repo
  - Mythbuntu Weekly fixes enabled
  - Has Apple Trailers
  - No error on console when starting MCC


Thanks,

Lindsay

---

### Post by sgtstadanko on 2008-11-04
another thin you may want to look for is there is a movie "Harold & Mike" I beleive.  The "&" symbol is killing the script and mythfrontend everytime I pull up the trailer page.  I had to modify the script to replace "&" with "and"  and it works.

---

