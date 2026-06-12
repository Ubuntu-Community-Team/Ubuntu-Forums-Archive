---
title: "Update Problems"
date: 2010-09-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by CoolJohnB on 2010-09-16
When I run an update by Synaptic or Terminal, I get the following errors:


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release](http://archive.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release](http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release](http://archive.canonical.com/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/Release](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Is there a solution to this?

Any help would be much appreciated, Thanks

---

### Post by CoolJohnB on 2010-09-17
Solved the problem by doing this:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com <hex number from the error output>

---

### Post by areteichi on 2010-09-24
Is there any other way to access the keyserver??? My internet connection is secured by the university and I cannot seem to be able to access the keyserver... Does anyone know how to work around this issue?

---

### Post by ktp on 2010-09-24
you can download/save the key file and manually import it.
> Get the key by going to keyserver.  Here is example for the [Ubuntu Archive Automatic Signing Key]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x40976EAF437D05B5")
Copy the everything starting from and including "-----BEGIN PGP PUBLIC KEY BLOCK-----"
Save it to text file.
Open System -> Administration -> Software Sources
Switch tabs to  Authentication
Click Import Key File&#8230;
Look for the file you saved the key to
Click OK

---

### Post by areteichi on 2010-09-25
The problem is that I cannot even access the link you provided: <[Ubuntu Archive Automatic Signing Key]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x40976EAF437D05B5")>
Why? Don't ask me.
Do you know any alternatives?

I will ask the IT department if they can do anything about this. Though I doubt they can...

---

### Post by cariboo on 2010-09-25
Do you have a firewall turned on?

---

### Post by CoolJohnB on 2010-09-25
> **ktp said:**
> you can download/save the key file and manually import it.

There are two steps missing to find software sources, it should be:

System>Administration>Update Manager>Settings>Software Sources

Hope that helps.

---

### Post by ktp on 2010-09-25
> **areteichi said:**
> The problem is that I cannot even access the link you provided: <[Ubuntu Archive Automatic Signing Key]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x40976EAF437D05B5")>
Why? Don't ask me.
Do you know any alternatives?

I will ask the IT department if they can do anything about this. Though I doubt they can...

IT might be best, if everyone in the university is seeing the same thing.  They might have firewall blocking it.  If so, then you are out of luck.

You could download the key form outside university network, but then you are most likely not going to any updates so useless.

---

### Post by efflandt on 2010-09-25
Do you have to use a proxy at the university?  If so, you might look at System > Preferences > Network Proxy to have it apply to all applications.

---

