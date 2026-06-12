---
title: "Full disk ecnryption"
date: 2008-06-06
forum: Mac OSX
---

### Post by hyper_ch on 2008-06-06
Does Mac OS X also have some kind of full disc encryption?

---

### Post by ilrudie on 2008-06-06
I believe its called file vault and can encrypt the whole disk.  I'm not on my mac at the moment so I can't say where the option is but if you poke around preferences for a little bit you will see it.  Start in the security area I'd say.  Hope that helps a bit.

---

### Post by hyper_ch on 2008-06-06
Well, it's a question for work... currently we are running here old mac systems and as there is an office move my boss decided also to upgrade the infrastructure and I shall present him some suggestins - and being in the legal business it seems to me wise to fully encrypt systems.

So, so far I've never worked on OS X before and my boss likes Mac as they have not given him any problems up to now :)

---

### Post by x0as on 2008-06-06
Filevault only encrypts your home directory.  

[http://www.checkpoint.com/products/datasecurity/pc/](http://www.checkpoint.com/products/datasecurity/pc/)  is an option.

---

### Post by cprofitt on 2008-06-06
The checkpoint solution looks like an answer for you...

It is sad that Apple has not got some encryption feature, but they simple are not an enterprise targeted company. The fact that they use the TPM module (Trusted Platform Module) for the purpose of preventing non-Apple equipment from loading OS X instead of providing a method for hardware based full-disk encryption speaks volumes.

Here are a couple of articles about the topic:

[http://www.networkcomputing.com/showArticle.jhtml?articleID=193500189](http://www.networkcomputing.com/showArticle.jhtml?articleID=193500189)

[http://www.hackinthebox.org/modules.php?op=modload&name=News&file=article&sid=26850&mode=thread&order=0&thold=0](http://www.hackinthebox.org/modules.php?op=modload&name=News&file=article&sid=26850&mode=thread&order=0&thold=0)

If you are going to do it for security reasons full disk is the way to go. If the Apple product will allow you to leverage the TPM, which I suspect it can't because of how Apple has used it, then hardware full-disk encryption would be more secure than software, but it will be a cause of concern because if the motherboard fails the data is gone.

---

### Post by bashveank on 2008-06-06
Don't mean to hijack the thread, but everyone keeps saying that full disk encryption is the way to go, but why is that? How is full disk encryption stronger than just encrypting your home folder?

---

### Post by cprofitt on 2008-06-06
> **bashveank said:**
> Don't mean to hijack the thread, but everyone keeps saying that full disk encryption is the way to go, but why is that? How is full disk encryption stronger than just encrypting your home folder?

This will be a little technical but...

When files are encrypted they need to be decrypted... in the case of home directory only that means that virtual memory and real memory will be used to accomplish that. If a hacker were to get the computer they could look at the ram and file slack to find bits and pieces (some whole files) of the encrypted data.

[http://www.niiconsulting.com/checkmate/2006/06/file-slack-vs-ram-slack-vs-drive-slack/](http://www.niiconsulting.com/checkmate/2006/06/file-slack-vs-ram-slack-vs-drive-slack/)

The other issue is that software encryption will do little to protect passwords etc that are stored. I am not as experienced with how Macs store passwords, but on Windows machines if the home directory was the only thing encrypted most of the important data (possibly even the encryption password for the software based encryption) would be found.

---

### Post by AlphaMack on 2008-06-07
[http://citp.princeton.edu/memory/](http://citp.princeton.edu/memory/)

Encryption doesn't mean jack if the RAM contents can be recovered.

---

### Post by hyper_ch on 2008-06-07
One would firstly have to assume that there is an encryption there and get according equipement there and surprise you "during work".

---

