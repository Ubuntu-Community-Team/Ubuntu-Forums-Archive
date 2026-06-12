---
title: "wpa_supplicant connect to hidden essid"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by pokeyThePenguin on 2011-01-04
I've been struggling for hours to find a way to connect to my wireless router via the command line--the NetworkManager applet connects to it just fine. This is more of a study in how to do it manually because I'm trying to learn how to run Linux without X.

I have a hidden ESSID encrypted using WPA2-personal.

Something in the wpa_supplicant debug (-dd) output mentions something about keys not being configured. I guess wpa_supplicant is failing, and hence dhclient fails. Dhclient tries several intervals and then says "No DHCPOFFERS received."

I generated a psk using wpa_passphrase:
```

sudo wpa_passphrase MYESSID > /etc/wpa_supplicant/wpa_supplicant.conf
MYPASSWORD

```

This is what my wpa_supplicant.conf looks like:

```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
	ssid="MYESSID"
	scan_ssid=1
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP TKIP
	group=CCMP TKIP
	psk=SOMELONGSTRING
}

```

I have ap_scan=2 and scan_ssid=1 because I read that you need those variables set that way in order to connect to a hidden network.

Here's what I do when attempting to create a connection:
```

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "MYESSID"
sudo iwlist scan
sudo wpa_supplicant -B -c/etc/wpa_supplicant/wpa_supplicant.conf -iwlan0
sudo dhclient wlan0

```

Looking at my wpa_supplicant output, I see:
```

State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'MYESSID'
Cancelling scan request
...
No keys have been configured - skip key clearing
...

```

I've spent hours googling and reading about this problem. I'm stuck. I'd really appreciate any help.

---

### Post by pokeyThePenguin on 2011-01-04
I have an Atheros wireless card, which makes things tricky, I guess. I know I'm definitely running ath5k.

I read that ath5k names the wireless device wlan0, so that's fine. I assume not specifiying -D in wpa_supplicant defaults to the wext driver. I tried -Dmadwifi, but the output said that madwifi isn't supported.

My guess is that I need to be very picky with how I set up my wpa_supplicant.conf file, but I'm not exactly sure what I need to do.

Any ideas?

---

### Post by PatchesTheCaveman on 2011-01-04
Here's your problem:
```
sudo wpa_passphrase MYESSID > /etc/wpa_supplicant/wpa_supplicant.conf
``` won't work because you won't get root access when writing to the file.  To get root access for the whole command, run this:
```
sudo bash -c "wpa_passphrase MYESSID > /etc/wpa_supplicant/wpa_supplicant.conf"
```
That will execute the whole command as superuser.

---

### Post by pokeyThePenguin on 2011-01-04
I did that, but I'm still running into the same issues: No keys configured, scanning canceled.

My only guess is that this is a driver problem. -Dwext is the only option that makes an attempt at establishing a connection. I've tried -Dmadwifi and -Dath5k, but both say that those are unsupported, so wpa_supplicant terminates. I know ath5k has been loaded via modprobe.

I know I didn't make a typo with my password or ssid.

I notice this in the wpa_supplicant output: "WEXT: cfg80211-based driver detected."

And also:
```

EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0

```

```

State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'MYESSID'
Cancelling scan request
WPA: clearing own WPA/RSN IE
...
WPA: No WPA/RSN IE available from association info

```

```

wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)

```

---

### Post by pokeyThePenguin on 2011-01-04
I noticed that the output shows wpa_supplicant is always trying to authenticate with BSSID 00:00:00:00:00:00 but times out each time. No other BSSID's are used.

This led me to try to grab my BSSID by looking at iwlist scan, and then doing:

```

sudo iwconfig wlan0 ap ##:##:##:##:##:##

```

Then I run iwconfig, but it shows the BSSID didn't save, so I can't test this solution.

Other things I've noticed:

When my scan_ssid and ap_scan were set to scan non-hidden networks, wpa_supplicant would scan all my neighbours BSSID's. It also showed mine, but mine had ssid=''. iwlist scan also shows two entries for my router: one with an ssid set and one with a bunch of \x00 null values for the ssid.

My questions at this point are either (1) how do I get iwconfig to save the AP because I think this might get wpa_supplicant to work; or (2) how should I set my wpa_supplicant.conf to find hidden networks because what it's set to now only finds 00:00:00:00:00:00.

Thanks. I appreciate any help.

---

### Post by pokeyThePenguin on 2011-01-05
Well, I answered my second question myself:

```

sudo iwlist wlan0 scan essid MYESSID

```

That'll get your hidden ESSID to show up in your iwlist scan. Mine shows up when I'm in an X environment by simply doing "iwlist scan," but when I'm out of X, iwlist doesn't find the hidden network. Don't ask me why. I don't know, but the solution to that problem is what I wrote above.

However, that solution didn't help me. I guess wpa_supplicant doesn't want to pay attention to the iwlist scan results, which I thought it would.

This still leaves my first question in my previous post unanswered. I'm still unsure of how to set the AP. Whenever I run "sudo iwconfig wlan0 ap ##:##:##:##:##:##", the setting never sticks. iwconfig will continue to show "AP: Not-Associated."

Right now I'm wondering if I can pipe the iwlist results into wpa_supplicant like this:

```

sudo bash -c "iwlist wlan0 scan essid MYESSID | wpa_supplicant -B -c/etc/wpa_supplicant/wpa_supplicant.conf -iwlan0"

```

I'm going to try that now. I doubt it will work.

Any other ideas for connecting to a hidden network via the command line and wpa_supplicant?

---

### Post by pokeyThePenguin on 2011-01-06
Okay, I feel I'm getting very a close to a solution.

I did some more reading and found that for a hidden network, you need to add lots of specifics to your wpa_supplicant.conf. Here's what mine looks like:

```

ap_scan=2

network={
	ssid="YOURESSID"
	scan_ssid=1
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP
	group=CCMP
	psk=YOURPASSWORD
}

```

wpa_supplicant now finds my router's BSSID and tries to associate with it; however, it fails.

I think this is because wpa_supplicant is finding my router with a null ssid. I mentioned in my very first post how iwlist has a double entry for my router in its results: one with a null ssid and one with an ssid set.

I also found that you can set bssid in wpa_supplicant.conf, but this doesn't do anything more than the .conf above.

I'm going to try to just do ssid="" and set my bssid.

---

### Post by pokeyThePenguin on 2011-01-06
Attempted ssid of "" and \x00. Both didn't work.

The closest I've gotten to establishing a connection was with the wpa_supplicant.conf I wrote in my last post. What happens is my computer will try to associate with 00:00:00:00:00:00 a few times, and then wpa_supplicant will find my AP. It will try to associate with that, but then I get "New wireless event. New AP: 00:00:00:00:00:00," which cancels the association with my router and adds it to a blacklist.

I don't even know why this happens even if I explicitly set the bssid in my .conf.

What do you guys think?

---

### Post by pokeyThePenguin on 2011-01-08
Here's my latest .conf:

```

filter_ssids=1
ap_scan=2

network={
	ssid="REMOVED"
	scan_ssid=1
	bssid=REMOVED
	priority=100
	mode=0
	proto=RSN
	key_mgmt=WPA-PSK
	auth_alg=OPEN
	pairwise=CCMP
	group=CCMP
	psk=REMOVED
}

```

I get this as output:

```

Line 1: unknown global field 'filter_ssids=1'.
Line 1: Invalid configuration line 'filter_ssids=1'.

```

Of course no search results online yield anything helpful, so I downloaded the source code from here: [http://hostap.epitest.fi/releases/wpa_supplicant-0.7.3.tar.gz](http://hostap.epitest.fi/releases/wpa_supplicant-0.7.3.tar.gz). Then I did a grep for "unknown global field" and "Invalid configuration."

Here's a snippet of the relevant section (config_file.c, starting from line 472):

```

#define NUM_GLOBAL_FIELDS (sizeof(global_fields) / sizeof(global_fields[0]))


static int wpa_config_process_global(struct wpa_config *config, char *pos,
				     int line)
{
	size_t i;
	int ret = 0;

	for (i = 0; i < NUM_GLOBAL_FIELDS; i++) {
		const struct global_parse_data *field = &global_fields[i];
		size_t flen = os_strlen(field->name);
		if (os_strncmp(pos, field->name, flen) != 0 ||
		    pos[flen] != '=')
			continue;

		if (field->parser(field, config, line, pos + flen + 1)) {
			wpa_printf(MSG_ERROR, "Line %d: failed to "
				   "parse '%s'.", line, pos);
			ret = -1;
		}
		break;
	}
	if (i == NUM_GLOBAL_FIELDS) {
		wpa_printf(MSG_ERROR, "Line %d: unknown global field '%s'.",
			   line, pos);
		ret = -1;
	}

	return ret;
}

```

From what I understand, the "Invalid configuration" error is triggered by the "unknown global field" error, so solving the former solves the latter.

"Global fields" is a struct defined as:

```

static const struct global_parse_data global_fields[] = {
...
}

```

field_ssids is a field in that struct:

```

{ INT_RANGE(filter_ssids, 0, 1) }

```

I don't understand the code very well. My guess is that given a line as input, such as "filter_ssids" or "ap_scan," the function will loop through the global_fields struct looking for that field. If the field is not found in the struct, then the "unknown global field" error is thrown.

What's confusing me is that I have "filter_ssids" in my .conf and I see "filter_ssids" in the global_fields struct. I've made sure I didn't make a typo.

I figure if I can filter the scan results to only include my BSSID, I won't have the 00:00:00:00:00:00 problem anymore.

Anyone see something I don't see? Please....

====================================================================

wpa_supplicant -v shows that I have the previous stable version (0.6), not the current stable version (0.7). "filter_ssids" wasn't introduced until 0.7.

I'm going to try to grab 0.7 and see if that solves all my problems.

I really hope all my messages have been helpful to someone...

---

### Post by kevdog on 2011-01-08
Keep working at it, I'm interested in your results.  I'm surprised the bssid parameter doesn't work.  

Have you tested if you can connect when your network is unhidden?  Just want to make sure the entire wpa authentication/ handshake process is working prior to hiding the access point.

---

### Post by pokeyThePenguin on 2011-01-09
I definitely appreciate the encouragement.

Firstly, upgrading to v0.7 to get the filter_ssids functionality didn't help. The output was unaffected.

Since Ubuntu doesn't provide the latest wpasupplicant in the repo, here's how you upgrade:

```

1. Download http://hostap.epitest.fi/releases/wpa_supplicant-0.7.3.tar.gz
2. cd to directory you saved the tar.gz to
3. sudo tar -xvzf wpa_supplicant-0.7.3.tar.gz -C /usr/src/
4. cd /usr/src/wpa_supplicant-0.7.3/wpa_supplicant
5. sudo gedit .config
6. This Web page is helpful: http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap.git;a=blob_plain;f=wpa_supplicant/README.
Here's my .config, which compiled without any errors or warnings:

CONFIG_DRIVER_HOSTAP=y
CONFIG_DRIVER_WEXT=y
CONFIG_DRIVER_NDISWRAPPER=y
CONFIG_IEEE8021X_EAPOL=y
CONFIG_EAP_MD5=y
CONFIG_EAP_MSCHAPV2=y
CONFIG_EAP_TLS=y
CONFIG_EAP_PEAP=y
CONFIG_EAP_TTLS=y
CONFIG_EAP_GTC=y
CONFIG_EAP_OTP=y
CONFIG_EAP_SIM=y
CONFIG_EAP_AKA=y
CONFIG_EAP_PSK=y
CONFIG_EAP_SAKE=y
CONFIG_EAP_GPSK=y
CONFIG_EAP_PAX=y
CONFIG_EAP_LEAP=y
CONFIG_EAP_IKEV2=y

7. sudo make
Note that if the compilation doesn't go smoothly, remove the culprit from .config, type
"make clean," and try "make" again. I started with full features and
all drivers and then widdled that down to the .config above.

8. sudo cp wpa_cli wpa_supplicant /usr/local/bin

9. wpa_supplicant -v
This should spit out v0.7 now.

```

For some reason, the -foutputfile.txt option doesn't work for me in v0.7, so I just redirect the output using ">> outputfile.txt."

Here are the steps I did:

```

1. sudo iwconfig wlan0 essid "REMOVED"

2. iwconfig
(Make sure the essid was set)

3. sudo wpa_supplicant -dd -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dwext >> BEFORE.txt

```

After that, I changed ap_scan to =1, and scan_ssid to =0. Those values are the defaults, so I could have just commented those lines out for the same effect. I also tried one time with filter_ssids commented and one time with it uncommented. I went into my router settings and changed the hidden essid option to unhidden.

I also tried

```

sudo wpa_supplicant -B -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dwext

sudo dhclient wlan0

```

dhclient attempts many times to do its job and eventually gives up.

Now, unfortunately, no matter what I did, nothing allowed me to establish a connection.

In all the output files, I always notice AP 00:00:00:00:00:00. That AP always wants to interrupt my handshakes. I know that that AP isn't a real AP, but what is it? What's its source?

Perhaps the problem lies somewhere in the router settings?

---

### Post by pokeyThePenguin on 2011-01-10
I researched AP 00:00:00:00:00:00 a bit. I think this coupled with a null ssid is called a null probe response. Apparently this is used by attackers to render your router unusable. I don't think attackers are the only source of a null probe response. I haven't found any evidence, though.

After running "sudo iwconfig wlan0 essid 'FOOBAR'", I always check "iwconfig" to make sure the essid was set before I run wpa_supplicant. Well, I decided to check after as well and I noticed that after running wpa_supplicant, the essid for wlan0 is cleared. It's set back to "off/any."

Any ideas?

---

### Post by pokeyThePenguin on 2011-01-14
I'm all out of ideas.

Does anyone have any insights or ideas to add to this thread?

Does anyone experience the same problems? It'd be nice to know that I'm at least not alone.

---

### Post by BrixSat on 2011-10-24
Hey, you are not the only one out there. :) keep searching i will also do the same and post here some results!

---

### Post by BrixSat on 2011-11-22
I found that it is related to the driver. I moved to another card and the config you just outpuded works nicely,

---

### Post by pokeyThePenguin on 2011-12-04
Nice find!

So you're saying our network cards are simply unsupported?

---

