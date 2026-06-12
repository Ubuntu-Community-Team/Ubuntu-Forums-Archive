---
title: "configure modem for net zero"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by jeff35 on 2009-03-12
I can dial with netzero's runclient.sh program, but it cant find my modem.
how can I figure out where this info is going?

I can dial out with gnome ppp when runclient.sh has not been started, but cant connect to netzero.

then if i start runclient run client shuts down

this is the modem log:

--> Modem initialized.
--> Sending: ATM1L3DT3084022
--> Waiting for carrier.
ATM1L3DT3084022
CONNECT 460800 
--> Carrier detected.  Waiting for prompt.
GlobalPOPS
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: jeff
jeff
Password: 
--> Looks like a password prompt.
--> Sending: (password)
Request Denied
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: jeff
jeff
Password: 
--> Looks like a password prompt.
--> Sending: (password)
Request Denied
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: jeff
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
jeff
Password: 
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pp

this is my wvdial file:

[Dialer Defaults]
Phone = 3084022
Username = jeff8451
Password = faster
New PPPD = yes

I have tried changing 

New PPPD = /usr/sbin/pppd

I am stuck help plz



this is my pppd file:

multilink headersDon't use short sequence numbers in multilink headersEndpoint discriminator for multilinkDon't send or accept multilink endpoint discriminatorï¿½ï¿½ï¿½ï¿½ï¿½nnntt ï¿½ï¿½ ï¿½ï¿½    f   /ï¿½ï¿½8XEEE1ï¿½@ï¿½81ï¿½11111111ï¿½ï¿½h(ï¿½ï¿½ï¿½ï¿½Xxï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½`ï¿½QYaiqyï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½/etc/ppp/ip-pre-uplocal  IP address %Iremote IP address %Iaddrs %Icompress old-VJaddr %Ims-dns%d %Ims-wins %IRefused our IP addressDNS1DNS2USEPEERDNS/etc/ppp/resolv.confnameserver %s
Write failed to %s: %mOLDIPLOCALOLDIPREMOTEInterface failed to come upprimary   DNS address %Isecondary DNS address %Iinvalid netmask value '%s'unknown host: %sbad local IP address %sbad remote IP address %snoipDisable IP and IPCPnovjDisable VJ compression-vjnovjccomp-vjccompvj-max-slotsSet maximum VJ header slotsipcp-accept-localAccept peer's address for usipcp-accept-remoteAccept peer's address for itipparamSet ip script parameternoipdefaultms-dnsms-winsipcp-restartSet timeout for IPCPipcp-max-terminateSet max #xmits for term-reqsipcp-max-configureSet max #xmits for conf-reqsipcp-max-failureSet max #conf-naks for IPCPAdd default routenodefaultroutedisable defaultroute option-defaultrouteReplace default routenoreplacedefaultrouteNever replace default routeAdd proxy ARP entrynoproxyarpdisable proxyarp option-proxyarpusepeerdnsAsk peer for DNS address(es)set netmaskipcp-no-addressesipcp-no-addressDisable IP-Address usageIP addressesinvalid address parameter '%s' for ms-wins optioninvalid address parameter '%s' for ms-dns optionvj-max-slots value must be between 2 and 16Peer refused to agree to our IP addressCould not determine local IP addressCould not determine remote IP address: defaulting to %IPeer is not authorized to use remote address %IUnauthorized remote IP addressLocal IP address changed to %IRemote IP address changed to %IInterface configuration failedDisable VJ connection-ID compressionDon't use name for default IP adrsDNS address for the peer's useNameserver for SMB over TCP/IP for peerDisable old-style IP-Addresses usageset local and remote IP addressesQYaiqyï¿½ user= password=<hidden>Remote message: %0.*vPAP authentication failedPAPAuthReqAuthAckAuthNakhide-passwordDon't output passwords to logshow-passwordpap-restartpap-max-authreqpap-timeoutPAP authentication failed due to protocol-rejectPAP authentication of peer failed (protocol-reject)No response to PAP authenticate-requestscalling number %q is not authorizedPAP peer authentication failed for %qPAP peer authentication succeeded for %qShow password string in debug log messagesSet retransmit timeout for PAPSet max number of transmissions for auth-reqsSet time limit for peer PAP authenticationï¿½ï¿½ï¿½>, name = CHAP authentication failedCHAP authentication succeeded%s: %.*vSuccessFailurechap-restartSet timeout for CHAPchap-max-challengeSet max #xmits for challengechap-intervalSet interval for rechallengechapms-strip-domainCHAP authentication failed due to protocol-rejectNo CHAP secret found for authenticating us to %qPeer %q failed CHAP authenticationCHAP: authentication with peer already started!CHAP digest 0x%x requested but not availableCHAP: peer authentication already started!No CHAP secret found for authenticating %qStrip the domain prefix before the Usernameemï¿½Cinvalid parameter '%s' for deflate optiondeflate option values must be 0 or %d .. %ddeflate option value of %d changed to %d to avoid zlib buginvalid parameter '%s' for bsdcomp optionbsdcomp option values must be 0 or %d .. %dMPPE required but peer refusedLost compression sync: disabling compressionToo many MPPE errors, closing LCPMPPE required, but auth done in both directions.MPPE required but not availableMPPE required, but MS-CHAP[v2] auth not performed.MPPE required, but keys are not available.  Possible plugin problem?Disabling 40-bit MPPE; MS-CHAP LM not supportedMPPE required, but both 40-bit and 128-bit disabled.MPPE required, but kernel has no support.MPPE required but peer negotiation failedMPPE required but not available in kernelRefusing MPPE stateful mode offered by peer%s receive compression enabled%s transmit compression enabledRequest BSD-Compress packet compressiondon't allow Deflate compressionrequire MPPE 40-bit encryptiondon't allow MPPE 40-bit encryptionrequire MPPE 128-bit encryptiondon't allow MPPE 128-bit encryption%d,%d(none)Predictor 2Predictor 1MPPE 128-bit 40-bit stateless(old#)Deflate%s (%d/%d)Deflate%s (%d)BSD-Compress (%d/%d)BSD-Compress (%d)Method %d +U-C+C-D+D-L+L-S+S-M+M-H+Hmppe %s %s %s %s %s %s%s (%.2x %.2x %.2x %.2x)deflate%s %d method %d check %dbsd v%d %dpredictor 1predictor 2Lost compression syncToo many MPPE errorsCompression disabled by peer.MPPE disabled, closing LCPMPPE disabled by peerNo compression negotiatedMPPE disabled%s / %s compression enabledCCPCompressedResetReqResetAcknoccpDisable CCP negotiation-ccpnobsdcompdon't allow BSD-Compress-bsdcomprequest Deflate compressionnodeflate-deflatenodeflatedraftdon't use draft deflate #request Predictor-1nopredictor1don't allow Predictor-1-predictor1require-mpperequire MPPE encryption+mppenomppedon't allow MPPE encryptionrequire-mppe-40+mppe-40nomppe-40require-mppe-128+mppe-128nomppe-128nomppe-statefuldisallow MPPE stateful modeï¿½ï¿½ï¿½hhHoVHHHHHHHHHHHHHHHï¿½HHHHï¿½Hï¿½@Hï¿½xxQYaiqECPEncryptednoecpDisable ECP negotiation-ecpLCP downallow-number argumentallow-ip argumentgroup %s is unknown+ua file nameuserpasswdauthorized addresses/etc/ppp/pap-secrets/etc/ppp/chap-secrets/etc/ppp/srp-secrets-No network protocols runningAuthentication failedConnect time expiredTraffic limitLink inactive/etc/ppp/auth-down/etc/ppp/auth-upPEERNAME/dev/Connection terminated.Link terminated.Connect: %s <--> %sStarting negotiation on %speer refused to authenticateNo secret found for PAP loginno PAP secret found for %s@loginuser %s logged inLogin incorrect%d LOGIN FAILURES ON %s, %slogin failedLogin ok%s authentication succeedednoauthrequire-pap+paprequire-chap+chaprequire-mschap+mschaprequire-mschap-v2+mschap-v2refuse-paprefuse-chaprefuse-mschaprefuse-mschap-v2require-eaprefuse-eap+uaSet name for auth with peerusehostnameremotenamepapcryptPAP passwords are encryptedprivgroupallow-ipremotenumberallow-numbercannot stat secret file %s: %mWarning - secret file %s has world and/or group accessunable to reset uid before opening %s: %munable to regain privileges: %munable to open user login data file %sunable to read user login data file %scan't open indirect secret file %sno secret in indirect secret file %sinvalid address length %v in auth. address listinvalid address length syntax: %vunknown host %s in auth. address listinterface unit %d too large for subnet %vCan't open srp secret file %s: %mBy default the remote system is required to authenticate itself(because this system has a default route to the internet)The remote system (%s) is required to authenticate itselfThe remote system is required to authenticate itselfbut I couldn't find any suitable secret (password) for it to use to do so.(None of the available passwords would let it use an IP address.)Traffic limit reached. Limit: %u Used: %uTerminating connection due to lack of activity.peer from calling number %q authorizedauth_peer_success: unknown protocol %xUnable to obtain CHAP password for %s on %s from pluginCan't open chap secret file %s: %mSecret for %s on %s is too longpeer refused to authenticate: terminating linkFailed to authenticate ourselves to peerCan't open PAP password file %s: %mauth_withpeer_success: unknown protocol %xRequire authentication from peerDon't require peer to authenticateRequire PAP authentication from peerRequire CHAP authentication from peerRequire MS-CHAP authentication from peerRequire MS-CHAPv2 authentication from peerDon't agree to auth to peer with PAPDon't allow PAP authentication with peerDon't agree to auth to peer with CHAPDon't allow CHAP authentication with peerDon't agree to auth to peer with MS-CHAPDon't allow MS-CHAP authentication with peerDon't agree to auth to peer with MS-CHAPv2Don't allow MS-CHAPv2 authentication with peerRequire EAP authentication from peerDon't agree to authenticate to peer with EAPSet local name for authenticationGet PAP user and password from filePassword for authenticating us to the peerMust use hostname for authenticationSet remote name for authenticationUse system password database for PAPAllow group members to use privileged optionsSet IP address(es) which can be used without authenticationSet remote telephone number for authenticationSet telephone number(s) which are allowed to connect # oops: %d not %d
 %x??????%s %q		# (from %s)
%s # %s value (type %d??)		# (from %s)
pppd options in effect:
option list entrypppd version %s
%s: %s
plugin file path/usr/lib/pppd/2.4.4Couldn't load plugin %splugin_initpppd_versionPlugin %s loaded.Can't open log file %s: %mError reading %s: %m%s%s is disabled zero or%s value must be%s >= %d%s value must be%s <= %d%s value cannot be increasedoption argumentsecrets filecommand lineunrecognized option '%s'unable to regain privilegescall file name/etc/ppp/peers/CALL_FILEtty init file name/etc/ppp/options..ppprc%s/%sIncrease debugging level-dkdebugSet kernel driver debug levelnodetach-detachupdetachholdoffidlemaxconnectSet connection time limitTake options from a filecallnopersistTurn off persist optionDial on demand--versionShow version number--helpShow brief listing of options-hlogfilenolognologfdlinknameSet logical name for linkmaxfailnoktuneDon't alter kernel settingsconnect-delayunitdumpdryrunchild-timeoutip-up-scriptSet pathname of ip-up scriptip-down-scriptEnable multilink operationnomultilinkDisable multilink operationnompbundleBundle name for multilinkpluginpass-filteractive-filterset filter for active pktsmaxoctetsSet connection traffic limitmomo-directionmo-timeoutxxx # [don't know how to print value]error in active-filter expression: %s
error in pass-filter expression: %s
%s has no initialization entry pointWarning: plugin %s has no version informationPlugin %s is for pppd version %s, this is %sunable to drop permissions to open %s: %minvalid numeric parameter '%s' for %s optionwarning: word in file %s too long (%.20s...)%s%s set in %s cannot be overridden
%s%s from %s overrides command line%s%s cannot be changed after initializationusing the %s%s requires root privilegethe %s%s may not be changed in %s%s value must be%s between %d and %dIn secrets file: unrecognized option '%s'In secrets file: too few parameters for option '%s'too few parameters for option %sunable to drop privileges to open %s: %mWarning: can't open options file %s: %mCan't open options file %s: %mIn file %s: unrecognized option '%s'In file %s: too few parameters for option '%s'call option value may not contain .. or start with /Don't detach from controlling ttyDetach from controlling tty once link is upSet time in seconds before retrying connectionSet time in seconds before disconnecting idle linkAdd given domain name to hostnameTake options from a privileged fileKeep on reopening connection after closeAppend log messages to this fileSend log messages to this file descriptorDon't send log messages to any fileDon't send log messages to any file descriptorMaximum number of unsuccessful connection attempts to allowAlter kernel settings as necessaryMaximum time (in ms) to wait after connect script finishesPPP interface unit number to use if possiblePrint out option values after parsing all optionsStop after parsing, printing, and checking optionsNumber of seconds to wait for child processes at exitSet pathname of ip-down scriptLoad a plug-in module into pppdset filter for packets to passSet direction for limit traffic (sum,in,out,max)Check for traffic limit every N secondspppd version %s
Usage: %s [ options ], where options are:
	<device>	Communicate over the named device
	<speed>		Set the baud rate to <speed>
	<loc>:<rem>	Set the local and/or remote interface IP
			addresses.  Either one may be omitted.
	asyncmap <n>	Set the desired async map to hex <n>
	auth		Require authentication from peer
        connect <p>     Invoke shell command <p> to set up the serial line
	crtscts		Use hardware RTS/CTS flow control
	defaultroute	Add default route through interface
	file <f>	Take options from file <f>
	modem		Use modem control lines
	mru <n>		Set MRU value to <n> for negotiation
See pppd(8) for more options.
2;2;
    ;ï¿½;ï¿½:ï¿½:2;8J(Jï¿½Hï¿½Hï¿½HJï¿½Hï¿½Hï¿½Hï¿½Hï¿½Hï¿½Hï¿½Jï¿½Hï¿½Hï¿½Hï¿½Iï¿½Iï¿½Iï¿½Oï¿½Oï¿½Oï¿½Nï¿½NzNSNOpen ICMP %s -> %s
UDPOpen %s %s:%d -> %s:%d
demand frameCouldn't set up demand-dialled PPP interface: %mï¿½#ï¿½2$Fï¿½W6eï¿½tHï¿½ï¿½ï¿½Zï¿½Ó¾lï¿½ï¿½ï¿½~ï¿½ï¿½ï¿½ï¿½ï¿½3"ï¿½V,Gï¿½u>dÉœ@ï¿½Û¿Rï¿½ï¿½ï¿½dï¿½ï¿½ï¿½vï¿½!ï¿½0ï¿½&gï¿½v4Dï¿½UJï¿½Ã¼Xï¾‘ï¿½nï¿½ï¿½ï¿½|ï¿½ï¿½Ùƒ1
 ï¿½ï¿½w.fï¿½T<EË½Bï¿½ÙžPfï¿½ï¿½ï¿½tï¿½Bï¿½Saï¿½p ï¿½2'ï¿½6Lï¿½ï¿½ï¿½^ï¿½ï¿½ï¿½hï¿½ï¿½ï¿½zï¿½ï¿½ï¿½ï¿½R
                                                          Cï¿½q`ï¿½(ï¿½7:&ï¿½ï¿½Dï¿½ï¿½ï¿½Vï¿½ï¿½ï¿½`ï¿½ï¿½ï¿½rï¿½c@ï¿½Q"%ï¿½40ï¿½Nï¿½ï¿½ï¿½\ï¿½ï¿½ï¿½jï¿½ï¿½ï¿½xï¿½ï¿½ï¿½ï¿½sâ‰Â•PAÂ£5*$Â±8ÃÃ¿FÃ®ÃÃœTÃÃ«Â¹â‰Â¨Ã¹ÂšâŽ»Â„ÂÂ•Â§Â“Â¶,Ã‚Â¥Ã“>Ã¡Â·Ã°Ã‰R+Ã›:âNÃ*_â”´â””Ã¿â‰*Â‰Â” Â…Â›Â·Â¦Â*Ã’$ÃƒÂ¿Ã±6Ã*ÃH	Ã“;Z*Ã¥^â”ŒOÃ·Â£Â·â”Œ
Â¥ÂƒÂ´Â†Â‘Â—.Ã£Â§Ã²<Ã€ÂµÃ‘B)Ã‹8P
Ã™Â°âŽºÃ¯Â·â”œLÃ½]Â‹ÂµÂ¤Â™Â–Â‡Â¯Ã³&Ã¢Â½Ã4ÃÃƒ9J(Ã‘X
                                 Ã§â”¼â”¼Ãµ\â‰*M
                                         Ã†Â…Ã—Ã¥Â—Ã´(Â€Â¡Â‘:Â£Â³Â²DJÃ[Vâ‹ÃŸâ”‚â—†
                                                                 Ã©âŽ¼/Ã»>ÂÃ–Ã‡ÂŸÃµÃ¤Â©Ã³?â‰¥.Ã§Â‡Ã¶Ã„Â•Ã•*Â¡Â£Â°8Â‚Â±Â“Fâ”Ãâ‰¥THÃYâ‰-Ã«<âŽ»Ã¹ÂÃ·Ã¦ÂÃ”Ã…Â«Â±"Â*Â¹Â’0ÂƒÃ‡Ï€Nâ”˜Ã•X\IÃ£=â”˜,Ã±â”‚\%c\n\r\t\%.3o%d.%d.%d.%d[%s[%s data]%.8B ...[proto=0x%x]%.32B ...%s %P%10d
/var/lock%s/LCK..%sCan't create lock file %s: %mDevice %s is locked by pid %dï¿½jggggggï¿½jggggggjgggggggï¿½iggggggggggï¿½iï¿½igggggggciGig"iï¿½hï¿½hgï¿½hUhwgï¿½hgï¿½i0123456789abcdefCouldn't reopen lock file %s: %mCan't open existing lock file %s: %mCan't read pid from lock file %sRemoved stale lock on %s (pid %d)Couldn't remove stale lock on %seth0all had bit 7 set to 0all had odd parityall had even parityall had bit 7 set to 1Problem: %scould not open IPv6 socket/proc/etc/mtabignore/net/ipx/interface/net/ipx_interfaceCouldn't set MRRU: %m/dev/pppCouldn't open /dev/ppp: %musing channel %dCouldn't reopen /dev/ppp: %m/dev/ptmx/dev/pts/%d/dev/pty%c%xNo free pty for loopbackioctl(TIOCSETD): %m (line %d)tcsetattr: %m (line %d)read: %mread /dev/ppp: %m/proc/sys/kernel/modprobe/sbinPATHppp_genericppp0/net/routeifacedestinationgatewayflagseof on loopbackread from loopback: %m(%d)select: %mwrite: warning: %m (%d)write: %m (%d)tcgetattr: %m (line %d)speed %d not supportedtcflush failed: %mioctl(TIOCNXCL): %m (line %d)socket(AF_IPX): %m (line %d)ioctl(SIOCDARP): %m/sys/net/ipv4/ip_dynaddrSIOCGIFHWADDR(%s): %mioctl(SIOCSARP): %m/sys/net/ipv4/ip_forward/var/run/utmp/var/log/wtmpReceive serial link is not 8-bit clean:could not obtain hardware address for eth0Couldn't read compression error flags: %mIPX support is not present in the kernel
demand dialling is not supported by kernel driver version %d.%d.%dWarning: multilink is not supported by the kernel driverioctl(PPPIOCSNPMODE, %d, %d): %mFailed to set PPP kernel option flags: %mCouldn't set up TCP header compression: %mioctl(PPPIOCSDEBUG): %m (line %d)kernel does not support PPP filteringCouldn't set pass-filter in kernel: %mCouldn't set active-filter in kernel: %mCouldn't set channel receive MRU: %mCouldn't set MRU in generic PPP layer: %mCouldn't set channel receive asyncmap: %mioctl(set extended ACCM): %m (line %d)Couldn't set transmit async character map: %mioctl(SIOCGIFCONF): %m (line %d)internal error: file descriptor too large (%d)Couldn't attach to PPP unit %d: %mCouldn't create IP socket: %m(%d)in make_ppp_unit, already had /dev/ppp open?Couldn't set /dev/ppp to nonblock: %mCouldn't allocate PPP unit %d as it is already in useCouldn't create new ppp unit: %mCouldn't attach to interface unit %d: %m
Couldn't connect to interface unit %d: %mCouldn't get channel number: %mCouldn't attach to channel %d: %mCouldn't set /dev/ppp (channel) to nonblock: %mioctl(PPPIOCGUNIT): %m (line %d)transfer_ppp failed: wanted unit %d, got %dCouldn't set device to non-blocking mode: %mCouldn't make tty exclusive: %mioctl(transfer ppp unit): %m, line %dCouldn't set tty to PPP discipline: %mCouldn't reset tty to normal line discipline: %mCouldn't unlock pty slave %s: %mCouldn't open pty slave %s: %mcouldn't set attributes on pty: %mcouldn't get attributes on pty: %mcouldn't set master loopback to nonblock: %mcouldn't set slave loopback to nonblock: %mThis system lacks kernel support for PPP.  This could be because
the PPP kernel module could not be loaded, or because PPP was not
included in the kernel configuration.  If PPP was included as a
module, try `/sbin/modprobe -v ppp'.  If that fails, check that
ppp.o exists in /lib/modules/`uname -r`/net.
See README.linux file in the ppp distribution for more details.
pppd is unable to open the /dev/ppp device.
You need to create the /dev/ppp device node by
executing the following command as root:
	mknod /dev/ppp c 108 0
Couldn't determine if PPP is supported (no free ptys)ioctl(TIOCSETD(PPP)): %m (line %d)Couldn't read driver version: %mSorry, couldn't verify kernel driver version
Sorry - PPP driver version %d.%d.%d is out of date
can't open routing table %s: %mBaud rate for %s is 0; need explicit baud rateioctl(TIOCSETD, N_TTY): %m (line %d)Couldn't restore device fd flags: %mioctl(SIOCSIFADDR, IPX_DLTITF): %m (line %d)ioctl(SIOCDELRT) device route: %m (line %d)ioctl(SIOCSIFADDR): %m (line %d)ioctl (SIOCGIFFLAGS): %m (line %d)ioctl(SIOCSIFFLAGS): %m (line %d)Couldn't get PPP statistics: %mioctl(SIOCGIFMTU): %m (line %d)ioctl(SIOCSIFMTU): %m (line %d)ioctl(SIOCSIFADDR, CRTITF): %m (line %d)ioctl(SIOCSIFADDR, CRTITF): Address already existsIPv6 socket creation failed: %mcif6addr: ioctl(SIOCGIFINDEX): %m (line %d)cif6addr: ioctl(SIOCDIFADDR): %m (line %d)cif6addr: ioctl(SIOCDIFADDR): No such addresssif6addr: ioctl(SIOCGIFINDEX): %m (line %d)sif6addr: ioctl(SIOCSIFADDR): %m (line %d)sif6addr: ioctl(SIOCADDRT): %m (line %d)ioctl(SIOCSIFADDR): Address already existsioctl(SIOCSIFDSTADDR): %m (line %d)ioctl(SIOCSIFNETMASK): %m (line %d)ioctl(SIOCADDRT) device route: %m (line %d)Couldn't enable dynamic IP addressing: %mfound interface %s for proxy arpCannot determine ethernet address for proxy ARPCouldn't enable IP forwarding: %mrestoring old default route to %s [%I]restore default route ioctl(SIOCADDRT): %mnot replacing existing default route via %Ireplacing old default route to %s [%I]not replacing existing default route through %sdel old default route ioctl(SIOCDELRT): %m%.2x%.2x%.2x%.2x%.2x%.2xnetwork %snode compression %drouter proto %drouter name " \%.2xcompleteRIP NLSP NONE %0.6B/etc/ppp/ipx-downsifup failed (IPX)sipxfaddr failed/etc/ppp/ipx-upEnable IPXCP (and IPX)+ipxnoipxDisable IPXCP (and IPX)-ipxipx-networkSet our IPX network numberipxcp-accept-networkipx-nodeSet IPX node numberipxcp-accept-localAccept our IPX addressipxcp-accept-remoteAccept peer's IPX addressipx-routingSet IPX routing proto numberipx-router-nameSet IPX router nameipxcp-restartSet timeout for IPXCPipxcp-max-terminateipxcp-max-configureipxcp-max-failureSet max #conf-naks for IPXCPIPX router name must be alphanumeric or _IPX router name is limited to %d charactersinvalid parameter '%s' for ipx-node optionAccept peer IPX network numberSet max #xmits for IPXCP term-reqsSet max #xmits for IPXCP conf-reqs`ï¿½%ï¿½ï¿½ï¿½ï¿½ï¿½kï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½hï¿½ï¿½8ï¿½xï¿½8ï¿½8ï¿½ï¿½ï¿½pï¿½(ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½QYaiqyï¿½,oops # nothing escapedcan't escape character 0x%xCouldn't stat %s: %m%s is not a character devicedisconnect script failedSerial link disconnected.Error writing record file: %mstdinselectsetuid failedpppd (charshunt)ptynottyCouldn't allocate pseudo-ttyUnable to regain privilegesFailed to open %s: %mCan't create socket: %mCan't connect to %s: %mInitializer script failedSerial port initialized.Connect script failedFailed to reopen %s: %mSPEEDWelcome script failedSerial port device nametty speedBaud rate for serial portnolockDon't lock serial devicedisconnectwelcomeScript to welcome clientInput/output is not a ttyrecordnocrtsctsDisable hardware flow control-crtsctsnocdtrctsxonxoffmodemUse modem control linesDon't use modem control linesdatarateescapeescape parameter contains invalid hex number '%s'internal error: file descriptor too large (%d, %d, %d)Couldn't create record file %s: %mcouldn't set pty master to nonblock: %mcouldn't set %s to nonblock: %mcouldn't set stdout to nonblock: %mError reading standard input: %mError reading pseudo-tty master: %mError writing standard output: %mError writing pseudo-tty master: %mCan't fork process for character shunt: %mdemand-dialling is incompatible with nottyconnect script is required for demand-dialling
%s option precludes specifying device namepty option is incompatible with notty optionsocket option is incompatible with pty and nottyno device specified and stdin is not a ttyCouldn't stat default device %s: %mUnable to drop privileges before opening %s: %m
Couldn't reset non-blocking mode on device: %mCouldn't create pipes for record option: %mCan't parse host:port for socket destination%s: unknown host in socket optionSerial connection established.Lock serial device with UUCP-style lock fileA program to initialize the deviceA program to set up a connectionProgram to disconnect serial deviceScript to run on pseudo-tty master sideSend and receive over socket, arg is host:portRecord characters sent/received to fileSet hardware (RTS/CTS) flow controlSet alternate hardware (DTR/CTS) flow controlSet software (XON/XOFF) flow controlUse synchronous HDLC serial encodingMaximum data rate in bytes/sec (with pty, notty or record option)List of character codes to escape on transmission$tI <missing type> type=0x%x <Message  <No message> <Value%.*B> <Name  <No name>-%d <s%.*B> <Default g=2> <g%.*B> <Default N> <N%.*B> <B%.*B> E f<%X> <M2%.*B%s> <PN%.*B> <Challenge%.*B> <missing hint> <Suggested-type %02X (%s) <missing length> <A%.*B> <M1%.*B%s> <Response%.*B%s> <truncated>%8B...EAP: too many Requests sentEAP: no response to RequestsEAP: Identity prompt "%.*q"EAP: Notification "%.*q"EAP: unexpected MD5-ResponseEAP: unknown code %d receivedRequestIdentityNotificationMD5-ChallengeOTPGeneric-TokenRSADSSKEAKEA-ValidateTLSDefenderWindows 2000ArcotCiscoNokiaSRPInitialPendingClosedListenIdentifySRP1SRP2SRP3MD5ChallOpenSRP4BadAutheap-restarteap-max-sreqeap-timeouteap-max-rreqeap-interval`(ï¿½P@ï¿½EAP: timeout waiting for Request from peerEAP authentication failed due to Protocol-RejectEAP authentication of peer failed on Protocol-RejectEAP: received too many Request messagesEAP: empty Request message discardedEAP: unexpected Nak in Request; ignoredEAP: received MD5-Challenge with no dataEAP: MD5-Challenge with bad length %d (8..%d)EAP: no MD5 secret for auth to %qEAP: unknown authentication type %d; NakingEAP: discarding Response %d; expected ID %dEAP: empty Response message discardedEAP discarding unwanted Identify "%.q"EAP: unauthenticated peer name "%.*q"EAP unexpected Notification; response discardedEAP: Nak Response with no suggested protocolEAP: peer requesting unknown Type %dEAP: received MD5-Response with no dataEAP: MD5-Response with bad length %dEAP: no MD5 secret for auth of %qEAP: unknown Response type %d; ignoredEAP: packet too short: %d < %dEAP: packet has illegal length field %d (%d..%d)EAP unexpected success message in state %s (%d)EAP unexpected failure message in state %s (%d)EAP: peer reports authentication failureSet retransmit timeout for EAP Requests (server)Set max number of EAP Requests sent (server)Set time limit for peer EAP authenticationSet max number of EAP Requests allows (client)Set interval for EAP rechallengeAï¿½AAccess grantedAccess denied
Error: MD4Update MD already done.
Error: MD4Update called with illegal count value %d.%02xS= M=E=E=647 Account disabledE=649 No dialin permissionE=691 Authentication failureE=709 Error changing passwordE=646 Restricted logon hoursE=648 Password expiredS=%s M=%sE=691 R=1 C=%0.*B V=0 M=%sE=691 R=1 C=%0.*B V=0MS-CHAPv2 Success packet is badly formed.MS-CHAPv2 mutual authentication failed.Out of memory in chapms_handle_failureUnknown MS-CHAP authentication failure: %.*vMS-CHAP authentication failed: %vPeer request for LANMAN auth not supportedOn the client side, this is the receive key; on the server side, it is the send key.On the client side, this is the send key; on the server side, it is the receive key.Cï¿½IP:%IPPPD_PID=sending SIGHUP to process %dbundle link list not foundcreateupdatecouldn't %s bundle link listmultilink requiredbundle identifierBUNDLE="%q"/%vbundle links keyBUNDLE_LINKS=%sBUNDLEIFNAME=pppIFNAME=ppp%dLink attached to %sNew bundle %s createdMACphonebundle link list not found (iterating list)couldn't update bundle link list (removal)link entry already exists in tdboops, didn't get multilink on renegotiationoops, multilink negotiated only for receiveï¿½Tï¿½Invalid error codetdb_unlock: count is 0
tdb_reopen: open failed (%s)
TDB file
freelist top=[0x%08x]
hash=%d
freelist:lock failed in tdb_expand
Corrupt databaseIO ErrorLocking errorOut of memoryRecord existsLock exists on other keysRecord does not existtdb_mmap failed for size %d (%s)
tdb_oob len %d beyond internal malloc size %d
tdb_oob len %d beyond eof at %d
tdb_brlock failed (fd=%d) at offset %d rw_type=%d lck_type=%d
tdb_brlock timed out (fd=%d) at offset %d rw_type=%d lck_type=%d
tdb_brlock failed (fd=%d) at offset %d rw_type=%d lck_type=%d: %s
tdb_unlock: list %d invalid (%d)
tdb_unlock: An error occurred unlocking!
tdb_lock: invalid list %d for ltype=%d
tdb_lock spinlock failed on list %d ltype=%d
tdb_lock failed on list %d ltype=%d (%s)
tdb_reopen: munmap failed (%s)
tdb_reopen: WARNING closing tdb->fd failed!
tdb_reopen: fstat failed (%s)
tdb_reopen: file dev/inode has changed!
tdb_reopen: failed to obtain active lock
tdb_open_ex: can't open tdb %s write-only
tdb_open_ex: tdb_new_database failed!tdb_open_ex: could not open file %s: %s
tdb_open_ex: failed to get global lock on %s: %s
tdb_open_ex: failed to truncate %s: %s
tdb_open_ex: %s (%d,%d) is already open in this process
tdb_open_ex: failed to allocate lock structure for %s
tdb_open_ex: failed to clear spinlock
tdb_open_ex: failed to take ACTIVE_LOCK on %s: %s
tdb_open_ex: failed to close tdb->fd on error!
tdb_read failed at %d len=%d (%s)
rec_read bad magic 0x%x at offset=%d
tdb_write failed at %d len=%d (%s)
remove_from_freelist: not on list at off=%d
tdb_free: upfate_tailer failed!
tdb_free: right read failed at %u
tdb_free: right free failed at %u
tdb_free: left offset read failed at %u
tdb_free: left read failed at %u (%u)
tdb_free: left free failed at %u
tdb_free: update_tailer failed at %u
tdb_free record write failed at offset=%d
tdb_next_lock: On error unlock failed!
tdb_alloc_read malloc failed len=%d (%s)
tdb_firstkey: error occurred while tdb_unlocking!
tdb_traverse: key.dptr == NULL and unlock_record failed!
tdb_traverse: unlock_record failed!
tdb_delete: WARNING tdb_unlock failed!
tdb_nextkey: lock_record failed (%s)!
tdb_nextkey: WARNING tdb_unlock failed!
bad magic 0x%08x in free list
entry offset=[0x%08x], rec.rec_len = [0x%08x (%d)]
total rec_len = [0x%08x (%d)]
ERROR: failed to read record at %u
 rec: offset=%u next=%d rec_len=%d key_len=%d data_len=%d full_hash=0x%x magic=0x%x
ERROR: failed to read tailer at %u
ERROR: tailer does not match record! tailer=%u totalsize=%u
expand_file to %d failed (%s)
expand_file write of %d failed (%s)
rec_free_read non-free magic 0x%x at offset=%d - fixing
rec_free_read bad magic 0x%x at offset=%d
eIllegal interface identifier (local): %sIllegal interface identifier (remote): %slocal/remote LL address required for demand-dialling
Could not determine remote LL addressCould not determine local LL addresslocal and remote LL addresses are equalLocal LL address changed to %sRemote LL address changed to %sSet interface identifiers for IPV6Accept peer's interface identifier for usUse (default) IPv4 address as interface identifierUse uniquely-available persistent value for link local address+ipv6fe80::%sipv6_demand_conflocal  LL address %sremote LL address %s/etc/ppp/ipv6-down/etc/ppp/ipv6-upLLLOCALLLREMOTEsif6addr failedsifup failed (IPV6)addr %sIPV6CPIPV6Enable IPv6 and IPv6CPnoipv6Disable IPv6 and IPv6CP-ipv6ipv6cp-accept-localipv6cp-use-ipaddripv6cp-use-persistentipv6cp-restartSet timeout for IPv6CPipv6cp-max-terminateipv6cp-max-configureipv6cp-max-failureSet max #conf-naks for IPv6CPQYaiqyï¿½%02x%02x:%02x%02x:%02x%02x:%02x%02xcallback number option=0x%x delay = %d number = %scbcp_opencbcp_lowerupwant: %dphone no: %sCBCP packet is too smalllength: %dno callback alloweduser callback allowedaddress: %suser admin defined allowedcbcp_resp cb_type=%dcbcp_resp CONF_USERcbcp_resp CONF_ADMINcbcp_resp CONF_NOCBCP_RESP receivedpeer will call: %sCall me back, pleaseNoCallbackUserDefinedAdminDefinedListAsk for callbackCBCP packet: invalid length %dcbcp_recvreq: malformed packet (%d bytes left)callback number truncated to 250 charactersid doesn't match: expected %d recv %dcbcp_recvack: malformed packetï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½Aï¿½ï¿½0
<hï¿½ï¿½ï¿½ï¿½oï¿½ï¿½ï¿½ï¿½dï¿½                       ï¿½
z
  ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½oï¿½ï¿½ï¿½ï¿½oï¿½ï¿½ï¿½oÃ¦              Ã±"Ã±2Ã±BÃ±RÃ±â‰Ã±âŽ¼Ã±Â‚Ã±Â’Ã±Â¢Ã±Â²Ã±Ã‚Ã±Ã’Ã±Ã¢Ã±Ã²Ã±Ã²Ã²"Ã²2Ã²BÃ²RÃ²â‰Ã²âŽ¼Ã²Â‚Ã²Â’Ã²Â¢Ã²Â²Ã²Ã‚Ã²Ã’Ã²Ã¢Ã²Ã²Ã²Ã³Ã³"Ã³2Ã³BÃ³RÃ³â‰Ã³âŽ¼Ã³Â‚Ã³Â’Ã³Â¢Ã³Â²Ã³Ã‚Ã³Ã’Ã³Ã¢Ã³Ã²Ã³Ã´Ã´"Ã´2Ã´BÃ´RÃ´â‰Ã´âŽ¼Ã´Â‚Ã´Â’Ã´Â¢Ã´Â²Ã´Ã‚Ã´Ã’Ã´Ã¢Ã´Ã²Ã´ÃµÃµ"Ãµ2ÃµBÃµRÃµâ‰ÃµâŽ¼ÃµÂ‚ÃµÂ’ÃµÂ¢ÃµÂ²ÃµÃ‚ÃµÃ’ÃµÃ¢ÃµÃ²ÃµÃ¶Ã¶"Ã¶2Ã¶BÃ¶RÃ¶â‰Ã¶âŽ¼Ã¶Â‚Ã¶Â’Ã¶Â¢Ã¶Â²Ã¶Ã‚Ã¶Ã’Ã¶Ã¢Ã¶Ã²Ã¶Ã·Ã·"Ã·2Ã·BÃ·RÃ·â‰Ã·âŽ¼Ã·Â‚Ã·Â’Ã·Â¢Ã·Â²Ã·Ã‚Ã·Ã’Ã·Ã¢Ã·Ã²Ã·Ã¸Ã¸"Ã¸2Ã¸BÃ¸RÃ¸â‰Ã¸âŽ¼Ã¸Â‚Ã¸Â’Ã¸Â¢Ã¸Â²Ã¸Ã‚Ã¸Ã’Ã¸Ã¢Ã¸Ã²Ã¸Ã¹Ã¹"Ã¹2Ã¹BÃ¹RÃ¹â‰Ã¹âŽ¼Ã¹Â‚Ã¹Â’Ã¹Â¢Ã¹Â²Ã¹Ã‚Ã¹Ã’Ã¹Ã¢Ã¹Ã²Ã¹ÃºÃº"Ãº2ÃºBÃºRÃºâ‰ÃºâŽ¼ÃºÂ‚ÃºÂ’ÃºÂ¢ÃºÂ²Ãº                                                    Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿Ã¼                             !   T#   Ã¾%   '   )   -+   7-   B/   W1   â”¼3   Ï€5   Â‘9   Âž;   Â*=   Ã…?   ÃA   Ã*C   Ã®E   ,G   Ã½I   \K
                                                     M   O   Q   6S   XU   HW  âŒY   â¤[   Âˆâ–’   âŽ½âŒ   ÂˆâŠ   Â*Â±   Â¼â‹   Ã–âŽº   Ã°âŽ½   Ã   Ã»   Ã½   )  =  R  Â¬â”˜Ã›        ÂƒÃ›
  Ã°    1  Â–3  Â5  Â³Â  ÃÂƒ  ÃÂ…  <Â‡  âÂ‰  ÂˆâŒ   Â°âŠ   Ã¬Â±   â‹   @  Ã”@  Ã¼@  9@  UÃœ   @  â—†Ãœ
                    @  (!@  â”#@  â”¬%@  Â‡'@  Â•[@  L!Â€  â”Œ#Â€  Â%Â€  Â¤'Â€  Â´)Â€  Ã‚+Â€  Ã1Â€  Ã¹3Â€  Ã˜5Â€  =Â€  $?Â€  Ã¼AÂ€   CÂ€  Ã®EÂ€  @GÂ€  @IÂ€  âŽ»KÂ€  Â˜MÂ€  ^OÂ€  Â¸QÂ€  âŽ½SÂ€  Â‘UÂ€  Ã*WÂ€  Â*YÂ€  Ãƒ[Â€
             âŽºÂ€  @âŽ½Â€  ÃŸÃÂ€  Ã´Ã»Â€  âÃ½Â€  Â‚  ÂÃ¦     Â‚  ÂƒÃ›
Â‚  Â´5Â‚  Ã¤ÂÂ‚  DÂ…Â‚                                    Â‚  -Ãž
                  Â‡Â‚  8Â‰Â‚  Âˆ!Ã€  *#Ã€  \%Ã€  K'Ã€  Â€)Ã€  Â¨+Ã€  ÃŒ-Ã€  _[Ã€  Ã¸ÂÃ€  âŒ#Ã‚  (%Ã‚  Â·'Ã‚  T)Ã‚  â”‚âŽºÃ‚  Â¤ÂÃ‚  ÃÂƒÃ‚  ÃÂÃ„  Ã´        !Ã€  Ã°Â*PÂÃÃ° âŽ»    
                           0Ã°Ã*Pâ—†Ã°Â Â°ÂâŽ»            Ã‹    @Ã¨ Â·   ÃŠ<
                Ã€   ÃŠ<
Q                       â–’                         âŽ¼   â—†                Ã¤   ( Ã                Ã¢   P                                        !Â€  @Â°âŽ»ÂP  âŽ»       Ã‡TÃ*Ã* ï¿½ï¿½ï¿½=        Ã€Ã*P Ã*Â* Ã°Â°    Ã            Ã‡    Â³   Â¸                       ï¿½ ï¿½
ï¿½ï¿½>`#ï¿½ï¿½@`ï¿½ï¿½ï¿½d-ï¿½>
ï¿½1?ï¿½Sï¿½P@\ï¿½?ï¿½ï¿½ï¿½pï¿½0ï¿½ï¿½ï¿½?ï¿½Hï¿½0Hï¿½
         `
        \ï¿½
       j
      pï¿½
      ï¿½
     pï¿½
                  
                    Ã¨Ã¡                                              â”‚;
                       Â*                  Ã*   Ã*âŽ½
pï¿½                                         pï¿½ï¿½@
ï¿½ï¿½ï¿½ï¿½ï¿½

                   X   @                       ÃV   @                                                                                            âŽ»A                             A                             A           F                                          Ã¿                                                                          0                     @                        Â½    0                               0    @D                         Â°C                          C           @
   Â°=                                           Ã¿Ã¿Ã¿Ã¿            Ã¿Ã¿Ã¿Ã¿                            2      K   â”¼      Â†      Â–      Ãˆ      ,     X    Â°  	
   â—†	
             Ã€
    K      Â–  ï¿½ï¿½K    Â–  ï¿½           Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿   Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿Ã¿ 	
 Ã¿Ã¿Ã¿Ã¿        +Â€  âŽ»ÃŒPÃŒÃŒ0ÃŒÃ°Ã‹ÃÃ‹Â°Ã‹Â€Ã‡        >  Ã°Ã™ÃÃ’Ã€Ã‘Â°ÃÃÃšâ—†ÃÃ°ÃÂ*Ã— Ã—    @Ã                Câ–’â”¼ â”¼âŽºâ”œ ââŠâ”œâŠâŽ¼â””â‹â”¼âŠ â”¼âŠâ”œâ”¬âŽºâŽ¼â” â”¼â”¤â””â‰âŠâŽ¼                          CâŽºâ”¤â”Œâ â”¼âŽºâ”œ ââŠâ”œâŠâŽ¼â””â‹â”¼âŠ â”ŒâŽºâŒâ–’â”Œ IPX â”¼âŽºââŠ â–’âââŽ¼âŠâŽ½âŽ½            Â©
                                  Â©
                                   0                                                                                      Ã¿Ã¿Ã¿Ã¿                 â—†Ã¦
                   Ã*Ã¥  Ã°	                â””   Â´	                      Â´	                         Â¸	                        Â¼	                 Ã€	                        Ã„	 Ãˆ	                      ÃŒ	
                                                                 Ã˜	
               Ã	                         Â¬	                      Â¬	                        Â¬	Ã¿                        Â¬	Ã¿0                  Â¬	Ã¿0                          Ã¤                                                                         Ã”	                         Ã¥   PÃ¤Ø‰ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½p ï¿½ï¿½Wï¿½ï¿½Pp0ï¿½ï¿½`ï¿½ï¿½ï¿½ ï¿½ï¿½ï¿½pï¿½ ï¿½0ï¿½ï¿½     'Ã‚  Ã€ Ã*Q
pppd9ï¿½kï¿½.shstrtab.interp.note.ABI-tag.gnu.hash.dynsym.dynstr.gnu.version.gnu.version_r.rel.dyn.rel.plt.init.text.fini.rodata.eh_frame.ctors.dtors.jcr.dynamic.got.got.plt.data.bss.gnu_debuglink
+                             4ï¿½4Hï¿½H %hï¿½h8!ï¿½ï¿½ï¿½oï¿½ï¿½ï¿½
   dï¿½d!0(3ï¿½ï¿½ï¿½Iz;ï¿½ï¿½ï¿½oÃ¦Â°                 H   Ã¾Ã¿Ã¿âŽº   Ã«â”  Ã               W   	      Ã¤Ã«Ã¤â”                 â—†   	      Ã´Ã«Ã´â”  Ã˜
                                                                                    â‹         ÃŒÃ°ÃŒâŽ»  0                  â         Ã¼Ã°Ã¼âŽ»  Ã€	               âŽº         Ã€ÃºÃ€â‰¥  â‰*Ãš                â”¤         <<U                   Ï€       â—†â—†U @Â™                  Âƒ         Â*Ã®                   Â        Ã¬Ã®                  Â”         Ã´Ã®                  Â›         Ã¼Ã®              Â*          Ã¯ Ã°               Â©         Ã°Ã¯               Â®         Ã´Ã¯ â”‚                Â·         Â€Ã² 3                  Â½     Â% ,Ã•                 Ã‚              Â%
                                                                       â”˜âŠÂ°Â°@â”¤â‰â”¤â”¼â”œâ”¤:/â”¤âŽ½âŽ¼/âŽ½â‰â‹â”¼$ 


any ideas?

---

