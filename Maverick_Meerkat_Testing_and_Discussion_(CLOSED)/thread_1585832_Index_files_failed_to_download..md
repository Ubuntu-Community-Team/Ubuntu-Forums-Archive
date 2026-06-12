---
title: "Index files failed to download."
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tricia56 on 2010-10-01
I am getting this message when trying to update in 10.10 (was hoping the RC would fix but to no avail)


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


I dont know where to go with this, I have searched around and tried a few things, but it is little beyond my expertise. 

tricia

---

### Post by KoBiReds on 2010-10-01
try the following on terminal


sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

---

### Post by ronacc on 2010-10-01
there is no maverick medibuntu repo , They don't put one up until after release .

---

### Post by tricia56 on 2010-10-01
> **KoBiReds said:**
> try the following on terminal


sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192


Great that worked, thanks!  Knew it was simple but it was driving me doo lally

tricia

---

