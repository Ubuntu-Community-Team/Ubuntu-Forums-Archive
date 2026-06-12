---
title: "medibuntu repo problem?"
date: 2008-04-25
forum: Multimedia Software
---

### Post by scradock on 2008-04-25
I am trying to add the medibuntu repos to my sources, and keep getting an error trying to load the non-free packages. This appears using Update Manager or sudo apt-get 

```
*********:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
....
W: Failed to fetch http://packages.medibuntu.org/dists/hardy/Release  Unable to find expected entry  nonfree/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```
 Is there an error in the Release file, as suggested, or is there some error in my system? This is an almost-pristine 8.04 install (RC + latest updates) on a new partition.....

---

### Post by overdrank on 2008-04-25
> **scradock said:**
> I am trying to add the medibuntu repos to my sources, and keep getting an error trying to load the non-free packages. This appears using Update Manager or sudo apt-get 

```
*********:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
....
W: Failed to fetch http://packages.medibuntu.org/dists/hardy/Release  Unable to find expected entry  nonfree/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```
 Is there an error in the Release file, as suggested, or is there some error in my system? This is an almost-pristine 8.04 install (RC + latest updates) on a new partition.....
Hi and did you first and the repos to you sources list
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```

---

### Post by scradock on 2008-04-25
Yes, I did. I have also added the medibuntu repos using Software Sources, and the free packages are being downloaded fine. It's only the nonfree packages that are apparently unavailable......

---

### Post by scradock on 2008-04-27
OK - problem solved! The nonfree packages need to be called non-free, once that was right the update stopped crashing.........

---

