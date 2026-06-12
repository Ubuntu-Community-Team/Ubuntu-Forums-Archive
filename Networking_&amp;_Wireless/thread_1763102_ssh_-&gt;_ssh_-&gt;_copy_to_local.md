---
title: "ssh -&gt; ssh -&gt; copy to local"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by majest on 2011-05-20
I have an ssh connection from my local computer (Ubuntu) to a remote machine A, and an ssh connection from A to another machine B. All are running linux variants. I can't access B directly due to IP restrictions.

I want to copy files from B over to my local computer. Also, I am running a wireless network at home thru Windows... sounds complicated... so all I want to do is drag and drop the files I can see and access on B onto my desktop here, without bothering with IP addresses, ports and all that junk ;)

Is there a "pull" command, or something like that, that copies the file on whatever system you are on back to the local machine?

---

### Post by papibe on 2011-05-20
Maybe it's not answer you are looking for, but anyway: How about considering a service like Dropbox or Ubuntu One?

Regards.

---

### Post by majest on 2011-06-17
> **papibe said:**
> Maybe it's not answer you are looking for, but anyway: How about considering a service like Dropbox or Ubuntu One?


No, not interested in that. There must be a way to do it correctly ;) Copy and paste to clipboard is one way but seems so primitive!

---

### Post by pricetech on 2011-06-17
Who's IP restrictions are getting in your way ??  If all three computers are yours, I don't see why you can't access them any way you want.

---

### Post by majest on 2012-03-16
For future reference, this is the answer taken from [here]("http://superuser.com/a/320438"). The original request was how to secure copy a file on a local machine to a target machine through a proxy machine.

   local -> proxy -> target

You need to put this in your ~/.ssh/config file on local.machine, (creating the file if it does not exist)
  
```

Host target
            User          targetuser
            HostName      target.address
            ProxyCommand  ssh proxyuser@proxy.address nc %h %p 2> /dev/null   

```After saving the file, you can just use 
  
ssh target 

or

scp localfile target:

(note the colon at the end).

---

