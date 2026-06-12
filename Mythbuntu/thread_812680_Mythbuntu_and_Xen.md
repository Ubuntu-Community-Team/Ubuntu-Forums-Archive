---
title: "Mythbuntu and Xen"
date: 2008-05-30
forum: Mythbuntu
---

### Post by gushy on 2008-05-30
Anyone got any experience running Mythbuntu in a Xen PVM?

I need to streamline the number of systems I have running in my house, so I want to replace my knoppmyth MBE with a PVM on my server.

I'm not sure how well a Xen PVM would handle the TV cards (3x Nova-T) and I was hoping someone else might have tried this and could give me pointers.

---

### Post by bah1976 on 2008-05-30
I went the other way - I'm running VMWare server on my mythbuntu MBE, currently running a single XP VM.  It's there primarily so I can use Orb & for my online backup client (windows only).  It doesn't use any resources unless i'm using it.  I know that doesn't help, but I thought I'd share anyway...

---

### Post by mr_claus on 2008-05-31
i use mythbuntu backend inside of a virtual machine. at the first time i had trouble with the pci devices.

use the configuration setting (depends on your pci device number)
pci         = [ '02:06.0' ]
extra       = 'console=xvc0 swiotlb=force'

after the intial problems it worked until today.

---

### Post by gushy on 2008-06-01
excellent thanks for the tip.

Did you use Ubuntu for your Dom0?  I'm currently running CentOS for my Dom0 but I think when I move to my new server box I will use Ubuntu so that hopefully setting up an Ubuntu based DomU will be easier (I've never managed to get a non RH / Fedora DomU running under a CentOS Dom0).

---

### Post by reeja on 2008-07-08
Dear all,

I would like to install Mythbuntu backend-only in a domU on my Xen server. Since you seem to have it already running successfully I would be interested in how you managed to install Mythbuntu as a domU:

[LIST]
[*]What installation method did you use? debootstrap?
[*]how do you get access to the graphical set-up screen? I do not have X installed in my dom0, because I want to kick out my graphic card in the future running the server headless...
[/LIST]

Thanks for your help in advance!
Regards, reeja.

---

