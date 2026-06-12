---
title: "Checkpoint VPN"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by rpremuz on 2012-04-26
On **Ubuntu 11.10 64-bit** I've got the same problem with snx installed by the Check_Point_SNX_R66_HFA_01_For_Linux_800004013.sh script downloaded from [https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doShowproductpage&productTab=downloads&product=175&version=VPN%20Clients%20for%20Linux](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doShowproductpage&productTab=downloads&product=175&version=VPN%20Clients%20for%20Linux)

If I try to connect I get the following:
```
$ snx -s example.foo.bar -u username -g
Check Point's Linux SNX
build 800004013
Please enter your password:

SNX: Connection aborted.

```

The debug log in ~/snx.elg contains the following (line prefix removed):

[FONT="Courier New"]snx: starting debug - Fri Apr 27 19:10:16 2012

snx_browser::snx_browser(): called
snx_browser::auth: entering
gwinfo:gwinfo: entered!0x864e098
creating the ssl layer
talkssl::talkssl(): entered with chunk=512, opaque=f729e008, link_established=80d3ab0, link_failure=80d3a90, packet_receive=80d3a60, verify_gw=80d3ad0
talkssl::set_sslalg:  setting ssl alg to 2
connecting
talkssl:: init_ssl_neg: using 3DES
ckpSSLctx_New: prefs = 1a
CkpRegDir: Environment variable CPDIR is not set.
GenerateGlobalEntry: Unable to get registry path
isExist: ProxyEntity didn't initiated yet
talkssl::start_async: Creating a new connection
talkssl::start_async: Connecting to gw: 0x0abdc6c1, port: 443
fwasync_make_connection: c1c6bd0a/443: dowait is -1 sock is 5
talkssl::start_async: Connection created successfully
fwasync_conn_params: <c0a80164,56815> -> <c1c6bd0a,443>
talkssl::client_handler: state: CONN_INIT - entering
talkssl::client_handler: start ssl negotaition
talkssl::client_handler: start openSSL negotaition
ckpSSL_PrepareConnection: verify mode: 0
My SSL Ciphers:
Cipher List:
0: DES-CBC3-SHA            SSLv3 Kx=RSA      Au=RSA  Enc=3DES(168) Mac=SHA1

1: RC4-SHA                 SSLv3 Kx=RSA      Au=RSA  Enc=RC4(128)  Mac=SHA1

2: RC4-MD5                 SSLv3 Kx=RSA      Au=RSA  Enc=RC4(128)  Mac=MD5 

3: DES-CBC-SHA             SSLv3 Kx=RSA      Au=RSA  Enc=DES(56)   Mac=SHA1

talkssl::client_handler: Returning OK!!!
ckpSSL_NegotiateStep: current state = before/connect initialization
is_initialized: new process or forked
CkpRegDir: Environment variable CPDIR is not set.
GenerateGlobalEntry: Unable to get registry path
CkpRegDir: Environment variable CPDIR is not set.
GenerateGlobalEntry: Unable to get registry path
CkpRegDir: Environment variable CPDIR is not set.
GenerateGlobalEntry: Unable to get registry path
CkpRegDir: Environment variable CPDIR is not set.
GenerateGlobalEntry: Unable to get registry path
rand_add_seedfile: Failed to read seed from registry.: Operation not permitted
CkpRegDir: Environment variable CPDIR is not set.
GenerateGlobalEntry: Unable to get registry path
CkpRegDir: Environment variable CPDIR is not set.
GenerateGlobalEntry: Unable to get registry path
fwrand_write_seed: Failed to read seed from registry.: Operation not permitted
CkpRegDir: Environment variable CPDIR is not set.
GenerateGlobalEntry: Unable to get registry path
CkpRegDir: Environment variable CPDIR is not set.
GenerateGlobalEntry: Unable to get registry path
fwrand_write_seed: Failed to write seed.: Operation not permitted
ckpSSL_NegotiateStep: should retry.
ckpSSL_NegotiateStep: current state = SSLv3 read server hello A
ckpSSL_fwasync_connected: no connections err -3
fwasync_end_conn: scheduling the end of connection 5
fwasync_do_end_conn: closing connection 5 (conn=8655d28)
talkssl::end_handler: ending connection 
snx_browser::Failure: entering with code: 1
got link down!- exit
snx: quit.
snx_browser::~snx_browser: called
talkssl::~talkssl: delete link
talkssl::~talkssl: end
done
[/FONT]

According to [https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=skI3336](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=skI3336)
CPDIR should be set to **/opt/CPshared**
and the path of the registry file should be **/opt/CPshared/registry/HKLM_registry.data**
but the question is how to create its content?

Could someone with a working installation of snx (probably on Ubuntu 9.10 or older) check if the registry file actually exists and what does it contain?

-- rpr.

---

### Post by lisati on 2012-04-26
Split from [http://ubuntuforums.org/showthread.php?t=1221196](http://ubuntuforums.org/showthread.php?t=1221196) into own thread.

A lot can happen in the world of software in two years.

---

### Post by grebxom on 2012-05-02
In /some/ cases, the hints given here: [http://www.linuxhome.ch/linux/wie-man-den-checkpoints-ssl-network-extender-auf-linux-einsetzt/](http://www.linuxhome.ch/linux/wie-man-den-checkpoints-ssl-network-extender-auf-linux-einsetzt/) /might/ help (german only, translate.google is your friend).

This: [https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk65669](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk65669) is an eye-opener. 

I finally succeded with Firefox on Ubuntu 12.04/64 after manually installing the 32-bit PAM libraries (download here: [http://packages.ubuntu.com/km/precise/i386/libpam0g/download](http://packages.ubuntu.com/km/precise/i386/libpam0g/download), extract to some temp. dir. and copy the libraries over to /lib/i386-linux-gnu. Trying to install the .deb won't work, but keep in mind that the manually installed files must be manually removed if need be.)

This procedure will use the client software as provided by the site you connect to, results may therefore vary.

---

