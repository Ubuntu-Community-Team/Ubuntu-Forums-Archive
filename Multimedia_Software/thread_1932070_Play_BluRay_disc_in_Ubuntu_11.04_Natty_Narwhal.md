---
title: "Play BluRay disc in Ubuntu 11.04 Natty Narwhal"
date: 2012-02-26
forum: Multimedia Software
---

### Post by Keith_Beef on 2012-02-26
I'm having trouble playing BluRay discs in Natty.

When I put in a disc, it appears in Places, and I can look at the files on the disc.

I've been trying to follow a few threads on UbuntuForums and also the following.
[http://apcmag.com/how-to-play-blu-ray-in-linux.htm](http://apcmag.com/how-to-play-blu-ray-in-linux.htm)
[http://forum.doom9.org/showthread.php?t=123111](http://forum.doom9.org/showthread.php?t=123111)

Running dumphd didn't get me any results that I could see, so I ran it with sudo. Here's what I see in the Log window.

```
DumpHD 0.61 by KenD00

Opening Key Data File... OK
Initializing AACS... OK
Loading aacskeys library... OK
aacskeys library 0.4.0 by arnezami, KenD00
Loading BDVM... FAILED
bdvm.vm.BDVM
Automatic BD+ removal disabled, specify a Conversion Table manually to remove BD+ if necessary

Initializing source... 
Disc type found: Blu-Ray BDMV
Collecting input files...
Source initialized
Identifying disc... OK
DiscID : 6170726910EA80F15E4CB1715390E80C644E9D75
Searching disc in key database...
Error behind line 618: Invalid data at end
Disc not found in key database
Retrieving keys from source... 
aacskeys 0.4.0 by arnezami, KenD00

Current path:                   /home/xxxxxxxx/.dumphd

MKBv:                           8
Processing key:                 7A5F8A09F833F7221BD41FA64C9C7933
Encrypted C-value:              8683A3C020EA28C9247093AB50FE0296
Corresponding uv:               000000C3

Decrypted C-value:              CE238555296F6A92F4474DE8418D2026
Media key:                      CE238555296F6A92F4474DE8418D20E5

Encrypted verification data:    C2F9CB02779E0724349E6ADA38466950
Decr verif data should be:      0123456789ABCDEF
Decrypted verification data:    0123456789ABCDEF3944F25CB7B89388

Drive FW info:                  JL022011/07/29 14:27    
AACS Version:                   01
Number of concurrent AGIDs:     3
Supports BN generation:         NO
BN Block Count:                 0
Inserted medium AACS protected: YES

AGID:                           00

Host Private Key (Hpriv):       8C8647FE2A70EF0388EA9E43F432CC441C6B108C
Host certificate (Hcert):       0200005CFFFF000000AE00004142A5411F1E63F1
                                85581C876B939FB40B523BF69C004CA69E047606
                                EE5183C0ABEF1E7D04CB6E65260677E7B0573D08
                                E60957935503ED78F7E27B190B4A7CAFCBAFF4A2
                                836453ECF72E49668DAF1DB9
Host Nonce (Hn):                2923BE84E16CD6AE529049F1F1BBE9EBB3A6DB3C

AGID:                           00

The given Host Certficate / Private Key has been revoked by your drive.


ERROR: SENDHOSTCHAL: SK: 0x5, ASC: 0x6F, ASCQ: 0x00, errnr: -2


aacskeys ERROR: SENDHOSTCHAL: SK: 0x5, ASC: 0x6F, ASCQ: 0x00, errnr: -2
Failed retrieving keys from source
```

Any ideas what I need to do from here?

K.

---

### Post by wolfen69 on 2012-02-26
I know that the new VLC 2.0 has the ability to play Blu-Ray.

---

