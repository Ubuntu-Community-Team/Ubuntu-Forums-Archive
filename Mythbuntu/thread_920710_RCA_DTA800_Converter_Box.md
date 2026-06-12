---
title: "RCA DTA800 Converter Box"
date: 2008-09-15
forum: Mythbuntu
---

### Post by Bal_Zac on 2008-09-15
I bought one of those 10 dollar DTV converter boxes, because I'm going to wait until a cheap HDTV tuner card comes out, and more importantly a cheap HDTV.  So I had to treat this as a STB and get an IR blaster.  Well there's no lirc config file anywhere.  So I built an ir receiver and analyzed the remote using xmode and mode2, getting a bunch of raw codes which the guys over at lirc converted to something nice looking.  So, if anybody is ever looking for a config file for this converter box, as I haven't seen it on the lirc remote page on sourceforge, here it is
```
#
# The RCA DTA800 is a digital to analog converter box.
# brand: RCA
# model number DTA800b
#

begin remote

 name  RCA_DTA800b
 bits           24
 flags SPACE_ENC
 eps            30
 aeps          250

 header       3750  4206
 one           252  2240
 zero          252  1245
 ptrail        275
 gap    8292
 toggle_bit_mask 0x0

     begin codes
         1                        0x7318CE
         2                        0x7328CD
         3                        0x7338CC
         4                        0x7348CB
         5                        0x7358CA
         6                        0x7368C9
         7                        0x7378C8
         8                        0x7388C7
         9                        0x7398C6
         0                        0x7308CF
         -                        0x76189E
         menu                     0x7088F7
         info                     0x73C8C3
         ok                       0x7F480B
         up                       0x7598A6
         down                     0x7588A7
         left                     0x7568A9
         right                    0x7578A8
         ch+                      0x72D8D2
         ch-                      0x72C8D3
     end codes

end remote
```

---

### Post by DBANate on 2008-09-25
Hi Bal_Zac,

This is cool I didn't know folks were analyzing remotes.  I don't know anything about IR (Infra Red?) technology.  I've got a DTA800 and I'm looking for the programming codes for my Magnavox.  The remote was working perfectly until my 4 year old got a hold of it and jacked up the programming.  I threw away the sheet thinking I could just find the codes on the web if I ever needed them again.  Bad move.  No codes anywhere.

So can I use the (Hex?) codes you have here to figure out how to program the remote?

I'm a Database Admin not an Engineer so I may be out of my league.

Thanks,
Nathan

---

