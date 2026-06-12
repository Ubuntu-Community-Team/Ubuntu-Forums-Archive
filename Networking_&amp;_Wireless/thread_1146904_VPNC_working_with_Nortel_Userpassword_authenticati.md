---
title: "VPNC working with Nortel User/password authentication"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by Chudilo on 2009-05-03
I have been struggling to configure VPNC to work with my Nortel VPN concentrator for quite some time now. VPN setup at work is relatively simple. It is a user/password authentication without a group ID or a token card.

I have seen other people lurking around for a solution for a similar setup.
Today I finally got it working and decided to share it with the rest of you.

Hopefully one of the changes that I had to apply manually will make it in to the Nortel branch so that one extra step can be avoided.

It would also be nice if the Nortel branch was finally merged into the trunk but that probably won't happen for quite some time.

Prerequisites:
Make sure the following are installed :

[LIST=1]
[*] svn (try running "svn" in terminal). If it is not installed, it will most likely offer to install it for you. (Otherwise you can run "sudo apt-get install svn". (It can also be installed using synaptic)
[*] libgcrypt-dev library can be installed via "sudo apt-get install libgcrypt11-dev"
[/LIST]

Step 1: Create a directory where you plan to run vpnc from and go there.
Step 2: Run the following: "svn co http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel/" to checkout the latest Nortel branch code.
Step 3: Apply the patch provided in this email: [http://lists.unix-ag.uni-kl.de/pipermail/vpnc-devel/2009-January/002959.html]("http://lists.unix-ag.uni-kl.de/pipermail/vpnc-devel/2009-January/002959.html")
Hopefully this code makes it into the Nortel branch soon and you will not have to do this. For the time being; I have also provided that code in this message. Copy and Paste the following code into a temp text file (Ex: nortelpatch.txt)  in the vpnc directory where you ran svn checkout. 

```

Index: isakmp.h
===================================================================
--- isakmp.h	(revision 394)
+++ isakmp.h	(working copy)
@@ -486,4 +486,23 @@
 	ISAKMP_XAUTH_ATTRIB_CISCOEXT_VENDOR = 0x7d88 /* strange cisco things ... need docs! */
 };
 
+enum isakmp_modecfg_type_enum { /* draft-ietf-ipsec-isakmp-xauth-05.txt */
+	ISAKMP_MODECFG_TYPE_GENERIC,
+	ISAKMP_MODECFG_TYPE_RADIUS,
+	ISAKMP_MODECFG_TYPE_OTP,
+	ISAKMP_MODECFG_TYPE_NTDOMAIN,
+	ISAKMP_MODECFG_TYPE_UNIX,
+	ISAKMP_MODECFG_TYPE_SECURID,
+	ISAKMP_MODECFG_TYPE_AXENT,
+	ISAKMP_MODECFG_TYPE_LEEMAH,
+	ISAKMP_MODECFG_TYPE_ACTIVECARD,
+	ISAKMP_MODECFG_TYPE_DESGOLD,
+	ISAKMP_MODECFG_TYPE_TACACS,
+	ISAKMP_MODECFG_TYPE_TACACSPLUS,
+	ISAKMP_MODECFG_TYPE_SKEY,
+	ISAKMP_MODECFG_TYPE_NDS,
+	ISAKMP_MODECFG_TYPE_DIAMETER,
+	ISAKMP_MODECFG_TYPE_LDAP
+};
+
 #endif
Index: config.h
===================================================================
--- config.h	(revision 394)
+++ config.h	(working copy)
@@ -49,6 +49,7 @@
 	CONFIG_IPSEC_SECRET,
 	CONFIG_IPSEC_SECRET_OBF,
 	CONFIG_XAUTH_USERNAME,
+	CONFIG_XAUTH_PIN,
 	CONFIG_XAUTH_PASSWORD,
 	CONFIG_XAUTH_PASSWORD_OBF,
 	CONFIG_XAUTH_INTERACTIVE,
@@ -87,11 +88,16 @@
 };
 
 enum auth_mode_enum {
-	AUTH_MODE_PSK,
+	AUTH_MODE_PSK,                  /* pre-shared key */
 	AUTH_MODE_RSA1,
 	AUTH_MODE_RSA2,
-	AUTH_MODE_CERT,
-	AUTH_MODE_HYBRID
+	AUTH_MODE_CERT,                 /* Digital Certificate Authentication */
+	AUTH_MODE_HYBRID,               /* server certificate + xauth */
+	AUTH_MODE_NORTEL_USERNAME,      /* User Name and Password Authentication */
+	AUTH_MODE_NORTEL_TOKEN,         /* Group Security - Response Only Token - Use Passcode */
+	AUTH_MODE_NORTEL_PINTOKEN,      /* Group Security - Response Only Token - Use Two-Factor Card */
+	AUTH_MODE_NORTEL_TOKENSW,       /* Group Security - Response Only Token - Use SoftID Software */
+	AUTH_MODE_NORTEL_GPASSWORD      /* Group Security - Group Password Authentication */
 };
 
 extern const char *config[LAST_CONFIG];
Index: config.c
===================================================================
--- config.c	(revision 394)
+++ config.c	(working copy)
@@ -159,7 +159,7 @@
 
 static const char *config_def_auth_mode(void)
 {
-	return "psk";
+	return "default";
 }
 
 static const char *config_def_nortel_client_id(void)
@@ -247,6 +247,13 @@
 		"your username",
 		NULL
 	}, {
+		CONFIG_XAUTH_PIN, 1, 0,
+		NULL,
+		"Xauth PIN ",
+		"<ASCII string>",
+		"PIN for Nortel Two-Factor Authentication",
+		NULL
+	}, {
 		CONFIG_XAUTH_PASSWORD, 1, 0,
 		NULL,
 		"Xauth password ",
@@ -434,11 +441,17 @@
 		CONFIG_AUTH_MODE, 1, 1,
 		"--auth-mode",
 		"IKE Authmode ",
-		"<psk/cert/hybrid>",
+		"<default/cert/psk/hybrid/username/token/PIN-token/token-SW/gpassword>",
 		"Authentication mode:\n"
-		" * psk:    pre-shared key (default)\n"
-		" * cert:   server + client certificate (not implemented yet)\n"
-		" * hybrid: server certificate + xauth (if built with openssl support)\n",
+		" * default:   maps to vendor specific default mode\n"
+		" * cert:      server + client certificate (not implemented yet)\n"
+		" * psk:       Cisco pre-shared key (default for Cisco)\n"
+		" * hybrid:    Cisco server certificate + xauth (if built with openssl support)\n"
+		" * username:  Nortel User Name and Password Authentication\n"
+		" * token:     Nortel Group Security - Response Only Token - Use Passcode (default for Nortel)\n"
+		" * PIN-token: Nortel Group Security - Response Only Token - Use Two-Factor Card\n"
+		" * token-SW:  Nortel Group Security - Response Only Token - Use SoftID Software\n"
+		" * gpassword: Nortel Group Security - Group Password Authentication",
 		config_def_auth_mode
 	}, {
 		CONFIG_CA_FILE, 1, 1,
@@ -703,16 +716,79 @@
 		opt_nd = (config[CONFIG_ND]) ? 1 : 0;
 		opt_1des = (config[CONFIG_ENABLE_1DES]) ? 1 : 0;
 
+		if (!strcmp(config[CONFIG_VENDOR], "cisco")) {
+			opt_vendor = VENDOR_CISCO;
+		} else if (!strcmp(config[CONFIG_VENDOR], "netscreen")) {
+			opt_vendor = VENDOR_NETSCREEN;
+		} else if (!strcmp(config[CONFIG_VENDOR], "nortel")) {
+			opt_vendor = VENDOR_NORTEL;
+		} else {
+			printf("%s: unknown vendor %s\nknown vendors: cisco netscreen nortel\n",
+				argv[0], config[CONFIG_VENDOR]);
+			exit(1);
+		}
+
 		if (!strcmp(config[CONFIG_AUTH_MODE], "psk")) {
 			opt_auth_mode = AUTH_MODE_PSK;
 		} else if (!strcmp(config[CONFIG_AUTH_MODE], "cert")) {
 			opt_auth_mode = AUTH_MODE_CERT;
 		} else if (!strcmp(config[CONFIG_AUTH_MODE], "hybrid")) {
 			opt_auth_mode = AUTH_MODE_HYBRID;
+		} else if (!strcmp(config[CONFIG_AUTH_MODE], "username")) {
+			opt_auth_mode = AUTH_MODE_NORTEL_USERNAME;
+		} else if (!strcmp(config[CONFIG_AUTH_MODE], "token")) {
+			opt_auth_mode = AUTH_MODE_NORTEL_TOKEN;
+		} else if (!strcmp(config[CONFIG_AUTH_MODE], "PIN-token")) {
+			opt_auth_mode = AUTH_MODE_NORTEL_PINTOKEN;
+		} else if (!strcmp(config[CONFIG_AUTH_MODE], "token-SW")) {
+			opt_auth_mode = AUTH_MODE_NORTEL_TOKENSW;
+		} else if (!strcmp(config[CONFIG_AUTH_MODE], "gpassword")) {
+			opt_auth_mode = AUTH_MODE_NORTEL_GPASSWORD;
+		} else if (!strcmp(config[CONFIG_AUTH_MODE], "default")) {
+			switch (opt_vendor) {
+				case VENDOR_NORTEL:
+					opt_auth_mode = AUTH_MODE_NORTEL_TOKEN;
+					break;
+				case VENDOR_NETSCREEN:
+				case VENDOR_CISCO:
+				default:
+					opt_auth_mode = AUTH_MODE_PSK;
+					break;
+			}
 		} else {
-			printf("%s: unknown authentication mode %s\nknown modes: psk cert hybrid\n", argv[0], config[CONFIG_AUTH_MODE]);
+			printf("%s: unknown authentication mode \"%s\"\nknown modes: "
+				"default/cert/psk/hybrid/username/token/PIN-token/token-SW/gpassword\n",
+				argv[0], config[CONFIG_AUTH_MODE]);
 			exit(1);
 		}
+
+		if (((opt_vendor == VENDOR_NORTEL) &&
+			((opt_auth_mode != AUTH_MODE_CERT) &&
+			 (opt_auth_mode != AUTH_MODE_NORTEL_USERNAME) &&
+			 (opt_auth_mode != AUTH_MODE_NORTEL_TOKEN) &&
+			 (opt_auth_mode != AUTH_MODE_NORTEL_PINTOKEN) &&
+			 (opt_auth_mode != AUTH_MODE_NORTEL_TOKENSW) &&
+			 (opt_auth_mode != AUTH_MODE_NORTEL_GPASSWORD))) ||
+		    ((opt_vendor == VENDOR_CISCO) &&
+			((opt_auth_mode != AUTH_MODE_CERT) &&
+			 (opt_auth_mode != AUTH_MODE_PSK) &&
+			 (opt_auth_mode != AUTH_MODE_HYBRID))) ||
+		    ((opt_vendor == VENDOR_NETSCREEN) &&
+			((opt_auth_mode != AUTH_MODE_CERT) &&
+			 (opt_auth_mode != AUTH_MODE_PSK) &&
+			 (opt_auth_mode != AUTH_MODE_HYBRID)))) {
+			printf("%s: Auth Mode \"%s\" not valid for Vendor \"%s\"\n",
+				argv[0], config[CONFIG_AUTH_MODE], config[CONFIG_VENDOR]);
+			exit(1);
+		}
+
+		if (opt_auth_mode == AUTH_MODE_CERT ||
+		    opt_auth_mode == AUTH_MODE_NORTEL_TOKENSW) {
+			printf("%s: unimplemented Auth Mode \"%s\"\n",
+				argv[0], config[CONFIG_AUTH_MODE]);
+			exit(1);
+		}
+
 #ifndef OPENSSL_GPL_VIOLATION
 		if (opt_auth_mode == AUTH_MODE_HYBRID ||
 			opt_auth_mode == AUTH_MODE_CERT) {
@@ -783,17 +859,6 @@
 			}
 			opt_nortel_client_id = tmp;
 		}
-
-		if (!strcmp(config[CONFIG_VENDOR], "cisco")) {
-			opt_vendor = VENDOR_CISCO;
-		} else if (!strcmp(config[CONFIG_VENDOR], "netscreen")) {
-			opt_vendor = VENDOR_NETSCREEN;
-		} else if (!strcmp(config[CONFIG_VENDOR], "nortel")) {
-			opt_vendor = VENDOR_NORTEL;
-		} else {
-			printf("%s: unknown vendor %s\nknown vendors: cisco netscreen nortel\n", argv[0], config[CONFIG_VENDOR]);
-			exit(1);
-		}
 	}
 
 	if (opt_debug >= 99) {
@@ -810,6 +875,12 @@
 			continue;
 		if (config[CONFIG_XAUTH_INTERACTIVE] && i == CONFIG_XAUTH_PASSWORD)
 			continue;
+		if (opt_auth_mode == AUTH_MODE_NORTEL_USERNAME
+		    && (i == CONFIG_XAUTH_USERNAME || i == CONFIG_XAUTH_PASSWORD))
+			continue;
+		if (opt_auth_mode != AUTH_MODE_NORTEL_PINTOKEN
+		    && i == CONFIG_XAUTH_PIN)
+			continue;
 
 		s = NULL;
 		s_len = 0;
@@ -828,6 +899,11 @@
 		case CONFIG_XAUTH_USERNAME:
 			printf("Enter username for %s: ", config[CONFIG_IPSEC_GATEWAY]);
 			break;
+		case CONFIG_XAUTH_PIN:
+			printf("Enter PIN for %s@%s: ",
+				config[CONFIG_XAUTH_USERNAME],
+				config[CONFIG_IPSEC_GATEWAY]);
+			break;
 		case CONFIG_XAUTH_PASSWORD:
 			printf("Enter password for %s@%s: ",
 				config[CONFIG_XAUTH_USERNAME],
@@ -839,6 +915,7 @@
 		fflush(stdout);
 		switch (i) {
 		case CONFIG_IPSEC_SECRET:
+		case CONFIG_XAUTH_PIN:
 		case CONFIG_XAUTH_PASSWORD:
 			s = strdup(getpass(""));
 			break;
@@ -870,10 +947,14 @@
 		error(1, 0, "missing IPSec ID");
 	if (!config[CONFIG_IPSEC_SECRET])
 		error(1, 0, "missing IPSec secret");
-	if (!config[CONFIG_XAUTH_USERNAME])
-		error(1, 0, "missing Xauth username");
-	if (!config[CONFIG_XAUTH_PASSWORD] && !config[CONFIG_XAUTH_INTERACTIVE])
-		error(1, 0, "missing Xauth password");
+	if (opt_auth_mode != AUTH_MODE_NORTEL_USERNAME) {
+		if (!config[CONFIG_XAUTH_USERNAME])
+			error(1, 0, "missing Xauth username");
+		if (!config[CONFIG_XAUTH_PASSWORD] && !config[CONFIG_XAUTH_INTERACTIVE])
+			error(1, 0, "missing Xauth password");
+	}
+	if (opt_auth_mode == AUTH_MODE_NORTEL_PINTOKEN && !config[CONFIG_XAUTH_PIN])
+		error(1, 0, "missing Xauth PIN");
 	if (get_dh_group_ike() == NULL)
 		error(1, 0, "IKE DH Group \"%s\" unsupported\n", config[CONFIG_IKE_DH]);
 	if (get_dh_group_ipsec(-1) == NULL)
Index: vpnc.c
===================================================================
--- vpnc.c	(revision 394)
+++ vpnc.c	(working copy)
@@ -1110,17 +1110,10 @@
 	r->u.sa.proposals->u.p.prot_id = ISAKMP_IPSEC_PROTO_ISAKMP;
 
 	if (opt_vendor == VENDOR_NORTEL) {
-	auth = 0;
+		auth = 0;
 		if ((opt_auth_mode == AUTH_MODE_CERT) &&
 	        (supp_auth[auth].ike_sa_id != IKE_AUTH_RSA_SIG) &&
 			(supp_auth[auth].ike_sa_id != IKE_AUTH_DSS)) {
-		} else if ((opt_auth_mode == AUTH_MODE_HYBRID) &&
-		    (supp_auth[auth].ike_sa_id != IKE_AUTH_HybridInitRSA) &&
-			(supp_auth[auth].ike_sa_id != IKE_AUTH_HybridInitDSS)) {
-		} else if (supp_auth[auth].ike_sa_id == IKE_AUTH_HybridInitRSA ||
-			supp_auth[auth].ike_sa_id == IKE_AUTH_HybridInitDSS ||
-			supp_auth[auth].ike_sa_id == IKE_AUTH_RSA_SIG ||
-			supp_auth[auth].ike_sa_id == IKE_AUTH_DSS) {
 		} else {
 			for (crypt = 0; supp_crypt[crypt].name != NULL; crypt++) {
 				keylen = supp_crypt[crypt].keylen;
@@ -1284,7 +1277,10 @@
 		l->u.id.protocol = IPPROTO_UDP;
 		l->u.id.port = ISAKMP_PORT; /* this must be 500, see rfc2407, 4.6.2 */
 		if (opt_vendor == VENDOR_NORTEL) {
-			l->u.id.length = 24;
+			if (opt_auth_mode == AUTH_MODE_NORTEL_USERNAME)
+				l->u.id.length = 20;
+			else
+				l->u.id.length = 24;
 			l->u.id.data = xallocc(l->u.id.length);
 			gcry_md_hash_buffer(GCRY_MD_SHA1, l->u.id.data, key_id, strlen(key_id));
 			/* memcpy(l->u.id.data, key_id, strlen(key_id)); */
@@ -1629,7 +1625,10 @@
 			reject = ISAKMP_N_INVALID_ID_INFORMATION;
 
 		/* Decide if signature or hash is expected (sig only if vpnc is initiator of hybrid-auth */
-		if (reject == 0 && opt_auth_mode == AUTH_MODE_PSK && (hash == NULL || hash->u.hash.length != s->ike.md_len))
+		if (reject == 0 &&
+			((opt_auth_mode == AUTH_MODE_PSK) ||
+			 (opt_vendor == VENDOR_NORTEL && opt_auth_mode != AUTH_MODE_CERT)) &&
+			(hash == NULL || hash->u.hash.length != s->ike.md_len))
 			reject = ISAKMP_N_INVALID_HASH_INFORMATION;
 		if (reject == 0 && sig == NULL &&
 			(opt_auth_mode == AUTH_MODE_CERT ||
@@ -1744,7 +1743,8 @@
 			expected_hash = gcry_md_read(hm, 0);
 			hex_dump("expected hash", expected_hash, s->ike.md_len, NULL);
 
-			if (opt_auth_mode == AUTH_MODE_PSK) {
+			if ((opt_auth_mode == AUTH_MODE_PSK) ||
+				(opt_vendor == VENDOR_NORTEL && opt_auth_mode != AUTH_MODE_CERT)) {
 				if (memcmp(expected_hash, hash->u.hash.data, s->ike.md_len) != 0)
 					error(2, 0, "hash comparison failed: %s(%d)\ncheck group password!",
 						val_to_string(ISAKMP_N_AUTHENTICATION_FAILED, isakmp_notify_enum_array),
@@ -2228,7 +2228,6 @@
 	DEBUGTOP(2, printf("S5.1 xauth_start\n"));
 	/* This can go around for a while.  */
 	for (loopcount = 0;; loopcount++) {
-		uint16_t xauth_type_requested = 5;
 		struct isakmp_payload *rp;
 		struct isakmp_attribute *a, *ap, *reply_attr;
 		char ntop_buf[32];
@@ -2343,6 +2342,12 @@
 		reply_attr = NULL;
 		for (ap = a; ap && reject == 0; ap = ap->next)
 			switch (ap->type) {
+			case ISAKMP_XAUTH_02_ATTRIB_TYPE:
+				if (opt_auth_mode == AUTH_MODE_NORTEL_GPASSWORD)
+					reply_attr = new_isakmp_attribute_16(ISAKMP_XAUTH_02_ATTRIB_TYPE, ISAKMP_MODECFG_TYPE_RADIUS, reply_attr);
+				else
+					reply_attr = new_isakmp_attribute_16(ISAKMP_XAUTH_02_ATTRIB_TYPE, ISAKMP_MODECFG_TYPE_SECURID, reply_attr);
+				break;
 			case ISAKMP_XAUTH_06_ATTRIB_DOMAIN:
 			case ISAKMP_XAUTH_02_ATTRIB_DOMAIN:
 				{
@@ -2416,16 +2421,27 @@
 					memset(pass, 0, na->u.lots.length);
 				} else {
 					struct isakmp_attribute *na;
-					if (opt_vendor == VENDOR_NORTEL) {
-						na = reply_attr->next = new_isakmp_attribute(ISAKMP_XAUTH_02_ATTRIB_PASSCODE, /* reply_attr */ NULL);
+					if (opt_vendor == VENDOR_NORTEL
+					    && opt_auth_mode != AUTH_MODE_NORTEL_GPASSWORD)
+						na = new_isakmp_attribute(ISAKMP_XAUTH_02_ATTRIB_PASSCODE, reply_attr);
+					else
+						na = new_isakmp_attribute(ap->type, reply_attr);
+					reply_attr = na;
+					if (opt_vendor == VENDOR_NORTEL
+					    && opt_auth_mode == AUTH_MODE_NORTEL_PINTOKEN) {
+						int l_pin, l_pas;
+						l_pin = strlen(config[CONFIG_XAUTH_PIN]);
+						l_pas = strlen(config[CONFIG_XAUTH_PASSWORD]);
+						na->u.lots.length = l_pin + l_pas;
+						na->u.lots.data = xallocc(na->u.lots.length);
+						memcpy(na->u.lots.data, config[CONFIG_XAUTH_PIN], l_pin);
+						memcpy(na->u.lots.data + l_pin, config[CONFIG_XAUTH_PASSWORD], l_pas);
 					} else {
-						na = new_isakmp_attribute(ap->type, reply_attr);
-						reply_attr = na;
+						na->u.lots.length = strlen(config[CONFIG_XAUTH_PASSWORD]);
+						na->u.lots.data = xallocc(na->u.lots.length);
+						memcpy(na->u.lots.data, config[CONFIG_XAUTH_PASSWORD],
+							na->u.lots.length);
 					}
-					na->u.lots.length = strlen(config[CONFIG_XAUTH_PASSWORD]);
-					na->u.lots.data = xallocc(na->u.lots.length);
-					memcpy(na->u.lots.data, config[CONFIG_XAUTH_PASSWORD],
-						na->u.lots.length);
 					passwd_used = 1; /* Provide canned password at most once */
 				}
 				break;
@@ -2433,10 +2449,6 @@
 				;
 			}
 
-		if (opt_vendor == VENDOR_NORTEL) {
-			reply_attr = new_isakmp_attribute_16(ISAKMP_XAUTH_02_ATTRIB_TYPE, xauth_type_requested, reply_attr);
-		}
-
 		/* Send the response.  */
 		rp = new_isakmp_payload(ISAKMP_PAYLOAD_MODECFG_ATTR);
 		rp->u.modecfg.type = ISAKMP_MODECFG_CFG_REPLY;
@@ -2551,7 +2563,8 @@
 		rp->u.modecfg.attributes = a;
 		sendrecv_phase2(s, rp, ISAKMP_EXCHANGE_MODECFG_TRANSACTION, msgid, 0, 0, 0, 0, 0, 0, 0);
 	} else {
-		r_length = sendrecv(s,r_packet, sizeof(r_packet), NULL, 0, 0);
+		if (opt_auth_mode != AUTH_MODE_NORTEL_USERNAME)
+			r_length = sendrecv(s,r_packet, sizeof(r_packet), NULL, 0, 0);
 	}
 
 	/* recv and check for notices */
@@ -3802,18 +3815,22 @@
 	do {
 		DEBUGTOP(2, printf("S4 do_phase1\n"));
 		do_phase1(group_id, config[CONFIG_IPSEC_SECRET], s);
-		DEBUGTOP(2, printf("S5 do_phase2_xauth\n"));
 
 		if (opt_vendor == VENDOR_NORTEL) {
-			do_load_balance = do_phase2_xauth(s);
+			if (opt_auth_mode != AUTH_MODE_NORTEL_USERNAME) {
+				DEBUGTOP(2, printf("S5 do_phase2_xauth\n"));
+				do_load_balance = do_phase2_xauth(s);
+			}
 			DEBUGTOP(2, printf("S6 do_phase2_config\n"));
 			do_load_balance = do_phase2_config(s);
 			DEBUGTOP(2, printf("S6 do_phase2\n"));
 			do_phase2(s);
 		} else {
 			/* FIXME: Create and use a generic function in supp.[hc] */
-			if (s->ike.auth_algo >= IKE_AUTH_HybridInitRSA)
+			if (s->ike.auth_algo >= IKE_AUTH_HybridInitRSA) {
+				DEBUGTOP(2, printf("S5 do_phase2_xauth\n"));
 				do_load_balance = do_phase2_xauth(s);
+			}
 			DEBUGTOP(2, printf("S6 do_phase2_config\n"));
 			if ((opt_vendor == VENDOR_CISCO || opt_vendor == VENDOR_NORTEL) && (do_load_balance == 0))
 				do_load_balance = do_phase2_config(s);

```

Step 4: Apply the patch by executing "patch -i nortelpatch.txt" in that same directory. (You may be asked to install the patch utility, follow the same procedure as with svn)
Step 5: run "make" to compile the program
Step 6: Create a directory named /etc/vpnc
Step 7: Copy vpnc-script to /etc/vpnc
Step 8: Execute vpnc with sudo passing some variation of the following parameters that can later be stored in a config script:  
I used the following:
sudo ./vpnc --vendor nortel --gateway <my gateway> --domain <MYDOMAIN> --auth-mode username --username <myusername> --dh dh5

---

### Post by HarDX on 2010-12-01
Hi,

Have you patch for new revision vpnc-nortel 449 and Ubuntu 10.10?

Thanks

---

