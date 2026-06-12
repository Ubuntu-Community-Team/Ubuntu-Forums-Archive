---
title: "MythTV backend on Ubuntu 10.04 server 64-bit?"
date: 2010-06-27
forum: Mythbuntu
---

### Post by Erik-NA on 2010-06-27
Currently I am running Ubuntu 8.04-server 64-bit on an
Asus P5B-V motherboard with Intel Core quad 2.4GHz and 8GB RAM. It is used as a NAS for my home gigibit network and it is also running Vmware server with three virtual machines.

I am planning to move to Ubuntu 10.04-server 64-bit and also install MyhTv backend (on the host, not as a virtual machine). The goal is to watch Canal Digital (in Sweden) via satellite, both SD and HD-channels.

Is it possible to use Muthbuntu 10.04 on a Ubuntu 64-bit server installation without any desktop environment?

---

### Post by ian dobson on 2010-06-27
Hi,

Why not just install the myth-backend (and all dependancys) on a normal ubuntu server. That's what I did for my headless backend server.

You only need X to run myth-setup when you need to reconfigur your myth-backend, and you can remote into the server with a X session.

```

dpkg -l | grep myth
ii  libmyth-0.23-0                             0.23.0+fixes24158-0ubuntu2                      Common library code for MythTV and add-on mo
ii  libmythtv-perl                             0.23.0+fixes24158-0ubuntu2                      A PERL library to access some MythTV feature
ii  mythtv-backend                             0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (serve
ii  mythtv-common                              0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (commo
ii  mythtv-database                            0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (datab
ii  mythtv-transcode-utils                     0.23.0+fixes24158-0ubuntu2                      Utilities used for transcoding MythTV tasks
ii  mythweb                                    0.23.0+fixes24104-0ubuntu2                      Web interface add-on module for MythTV

```

Regards
Ian Dobson

---

### Post by joshoekstra on 2010-06-29
Do the mythvideo and mythmusic still show up in mythweb then? I'm planning on swtiching to server as well and these tabs are ones I like using.
Isn't JAMU tied in to the mythvideo package as well?

---

### Post by ian dobson on 2010-06-29
Hi,

I don't use mythmusic so I can say. But if the package is installed then it should show up in mythweb (if it's meant to).

Mythbuntu is nothing other than ubuntu with afew extra packages for mythtv/mcc for configuration of the mythtv system.

I use mythweb quite abit but I can't see anything from mythvideo  in it, (I have it installed on my frontend). Going to the recordings screen in mythweb I can download/stream the videos but I don't think that's what you mean.

Regards
Ian Dobson

---

### Post by joshoekstra on 2010-07-02
Nope, mythvideo and music are frontend packages which I won't be able to install on server(I think) and the mythweb-options are connected to those packages I guess. I'll just have to try it out in the next few weeks when I'm rebuilding it to be server instead of mythbuntu(what I'm using now)

---

