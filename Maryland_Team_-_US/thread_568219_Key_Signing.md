---
title: "Key Signing"
date: 2007-10-05
forum: Maryland Team - US
---

### Post by phr0ze on 2007-10-05
I think we should do key signing at our next meeting. 

Who's interested?

What do we need to do to prepare?

Thanks,
John

---

### Post by ChuckFrain on 2007-10-06
I'm interested. 

The one requirement is that you need to bring a legal photo id.

There's multiple ways to handle it. The basics of the choices that I think would work best are outlined below. 

1. Anyone who wants to have their key signed needs to bring a slip of paper (I use a self printed business card) with their GPG Key ID on it. We then exchange the paper and check each other's id's. 

2. Maintain a master list of who will be attending along with their gpg key id. Provide a checkbox to tick off when you have verified that person's key (by his/her verbal confirmation) and id.

We can also provide a 'party keyring' with the keys of the attendees on the website for a simple grab of the keys. The proper way to then handle the signed key is to send it to the person who owns the key. Some prefer not to have their keys on the keyservers. 

If you want to read more, I found the [key signing party how-to]("http://cryptnet.net/fdp/crypto/keysigning_party/en/keysigning_party.html") to be a very detailed summary.

---

### Post by phr0ze on 2007-10-09
Thanks, I have to figure out how to make a GPG key and I'll be all set. I'm sure ti's just a how-to in the wiki. Any suggestions on what to put on the business card? Like a check box, initial box, signature block, etc?

---

### Post by ChuckFrain on 2007-10-11
The short answer to generating a key is the command 'gpg --gen-key' and follow the prompts. Then make a backup and a key revocation certificate. The cert should also be backed up to a different media than the key. Then I would upload the public key to a key server for it to be propagated out. 

If you're looking for a good frontend I've been happy with [ Seahorse]("http://www.gnome.org/projects/seahorse/") for some time now. Most mail programs for linux have some sort of plugin for GPG for integration. Some are better than others of course.

As for the card, I would put your name, email address, and website if you have one. I put my entire key fingerprint on it, however for the next run it will just be the Key ID (last eight characters of the key). Then I put a line that says 'verified' with a check box or line.

---

### Post by phr0ze on 2007-10-12
Thanks for the seahorse suggestion. It was real easy. Hardest part was using google to look up the ubuntu key server address. heh. not that hard.

---

### Post by Benanov on 2007-10-13
I'll try to be there. It'll be nice to have some signatures on my key that aren't mine.

The ubuntu keyserver thing is a bug--it should be fixed in Gutsy.

---

