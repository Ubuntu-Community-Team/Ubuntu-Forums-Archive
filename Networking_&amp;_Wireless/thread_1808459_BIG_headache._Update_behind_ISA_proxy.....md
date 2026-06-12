---
title: "BIG headache. Update behind ISA proxy...."
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by WanchoPiskado on 2011-07-20
Hey there.
I am running Ubuntu 10.04 LTS. Using Likewise Open I am connected to the active directory.
Our ISA server gives me a big headache.
I want to do updates with update manager. I want to install software using Ubuntu Software Center. I know there are two options:
1: editing /etc/apt/apt.conf and putting in username: password@proxy: port. Not doing this. Now everyone can see may password.
2: using NTLMAPS: [http://ubuntuforums.org/showpost.php?p=3340662&postcount=25](http://ubuntuforums.org/showpost.php?p=3340662&postcount=25)
Not doing this because NTLM is no longer recommended:
* Implementers should be aware that NTLM does not support any recent  cryptographic methods, such as AES or SHA-256. It uses cyclic redundancy  check (CRC) or message digest algorithms (RFC1321) for integrity, and  it uses RC4 for encryption. Deriving a key from a password is as  specified in RFC1320 and FIPS46-2. Therefore, applications are generally  advised not to use NTLM.*[***]("http://msdn.microsoft.com/en-us/library/cc236715%28v=PROT.10%29.aspx")
Is there a way to do this without using the options mentioned above?

Cheers!

---

### Post by WanchoPiskado on 2011-07-29
Oh well.
I'm gonna talk to my ad min to kill that headache i call ISA 
Cheers

---

