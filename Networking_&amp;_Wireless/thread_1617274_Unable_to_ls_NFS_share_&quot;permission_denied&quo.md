---
title: "Unable to ls NFS share &quot;permission denied&quot;"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by jarthurs on 2010-11-09
I have a Acer Altos EasyStore NAS on which I have enabled an NFS share for a specific IP address. The EasyStore then shows me the NFS path as:

Mount path: /nas/NASDisk-00004/media

When I try mounting the share from the machine at the allowed IP address it appears to mount OK, but when I try to view the directory using 'ls' I get 'ls: cannot open directory /nfs: Permission Denied'.

the /nfs folder where I'm trying to mount the NFS share shows up in ls as belonging to a group called 11587 (everything else is shown as root). I have no control over the group ID on the NAS as it's just an appliance.

How can I gain access to the shared folders?

Thanks,
Jason.

---

### Post by jarthurs on 2010-11-09
> **jarthurs said:**
> I have a Acer Altos EasyStore NAS on which I have enabled an NFS share for a specific IP address. The EasyStore then shows me the NFS path as:

Mount path: /nas/NASDisk-00004/media

When I try mounting the share from the machine at the allowed IP address it appears to mount OK, but when I try to view the directory using 'ls' I get 'ls: cannot open directory /nfs: Permission Denied'.

the /nfs folder where I'm trying to mount the NFS share shows up in ls as belonging to a group called 11587 (everything else is shown as root). I have no control over the group ID on the NAS as it's just an appliance.

How can I gain access to the shared folders?

Thanks,
Jason.

I've managed to use:

chmod -R go+rw /nfs 

then 

chmod 777 /nfs 

This appears to have given me full access to the files on the NAS. Not sure if this is an ugly hack, but it was a case of try and turn the permissions to give me access.

Regards,
Jason.

---

