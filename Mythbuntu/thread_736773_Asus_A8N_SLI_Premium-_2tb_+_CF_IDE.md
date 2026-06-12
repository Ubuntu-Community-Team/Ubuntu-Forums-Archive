---
title: "Asus A8N SLI Premium- 2tb + CF/ IDE?"
date: 2008-03-27
forum: Mythbuntu
---

### Post by purduephotog on 2008-03-27
I finally, with lots of fumbling, my A8N SLI Premium to run DVDs, video, and sound thru the optical SPDIF.  It required the nvidia proprietary driver to stop the screen from refreshing, but it works...

Now I need to figure out where to go from here.  The board is not what you'd call small- so it's going to be in an obtrusive case until it warms up enough for the woodshop work.

I originally installed everything on a 60gb HD with the intention of moving it off onto a flash stick or a CF/ IDE card for quiet. 

1) What's the easiest way to strip down everything that I don't need right now (install looks to be 30gb - 25gb or about 5gb total) to get it on a small flash card?

2) Anyone used one of these adapters to do so? [http://cgi.ebay.com/Dual-CF-2x-Compact-Flash-to-IDE-ATA-Converter-Adapter_W0QQitemZ170204821609QQihZ007QQcategoryZ41994QQssPageNameZWDVWQQrdZ1QQcmdZViewItem]("http://cgi.ebay.com/Dual-CF-2x-Compact-Flash-to-IDE-ATA-Converter-Adapter_W0QQitemZ170204821609QQihZ007QQcategoryZ41994QQssPageNameZWDVWQQrdZ1QQcmdZViewItem")

3) I've reviewed the LVM work and it seems like quite a bit, especially given the uncertainty if a drive fails.  I believe I'd rather mount one HD as a subfolder under another.  Suggestions as to how to do this?  Name one folder 'series' and the other 'movies' ? (Mash for instance is 33 disks, stargate is what, 55?... going to need WAY more space)

4) I need to enable power saving on this system but haven't found a way to do so yet.  I'd prefer something deep but spinning down the HDs is my first priority.  DPMS in Unix I know, but Linux...

Thanks in advance-

---

### Post by nasha on 2008-03-27
I can only help you out with one of your questions, as im not sure how mythbuntu would go with CF.

```
3) I've reviewed the LVM work and it seems like quite a bit, especially given the uncertainty if a drive fails. I believe I'd rather mount one HD as a subfolder under another. Suggestions as to how to do this? Name one folder 'series' and the other 'movies' ? (Mash for instance is 33 disks, stargate is what, 55?... going to need WAY more space)
```

MythTV 0.21 has introduced a new feature called Storage Groups which makes adding HDD a breeze: No more LVM
Add your hdd, partition and mount it as normal, then run mythtv-setup and go into Storage Groups (option number 6 i think), and place the location of the new mounted hdd there. Myth will then use this for recordings :)

---

### Post by purduephotog on 2008-03-29
> **nasha said:**
> I can only help you out with one of your questions, as im not sure how mythbuntu would go with CF.

```
3) I've reviewed the LVM work and it seems like quite a bit, especially given the uncertainty if a drive fails. I believe I'd rather mount one HD as a subfolder under another. Suggestions as to how to do this? Name one folder 'series' and the other 'movies' ? (Mash for instance is 33 disks, stargate is what, 55?... going to need WAY more space)
```

MythTV 0.21 has introduced a new feature called Storage Groups which makes adding HDD a breeze: No more LVM
Add your hdd, partition and mount it as normal, then run mythtv-setup and go into Storage Groups (option number 6 i think), and place the location of the new mounted hdd there. Myth will then use this for recordings :)

I went to that option and didn't find the storage groups; I ended up adding additional paths with the :.  That worked out pretty well, but navigation is tough with all the TV series.

I'm exploring the possibility of using a MD to hold everything; I found 5gb MD's for 10$ which would make it a pretty attractive option.

---

