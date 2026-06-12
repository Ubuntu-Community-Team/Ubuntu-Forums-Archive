---
title: "Help moving WPA2-enterprise connention from Win7 to Ubuntu 11.10"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by aragagg on 2012-02-28
Hi!

I simply didn't like the restriction my schools IT-department put on our computers so i decided to install a dualboot-solution with ubuntu.

My only problem is that i have a hard time connecting to the WPA2-enterprise connection with ubuntu, here's the config exported from windows, could anyone give me step-by-step instructions (Yes i am a linux-noob :D) 

```

<?xml version="1.0"?>
<WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
	<name>XXXX</name>
	<SSIDConfig>
		<SSID>
			<hex>XXXXXXXX</hex>
			<name>XXXX</name>
		</SSID>
		<nonBroadcast>false</nonBroadcast>
	</SSIDConfig>
	<connectionType>ESS</connectionType>
	<connectionMode>auto</connectionMode>
	<autoSwitch>true</autoSwitch>
	<MSM>
		<security>
			<authEncryption>
				<authentication>WPA2</authentication>
				<encryption>AES</encryption>
				<useOneX>true</useOneX>
			</authEncryption>
			<PMKCacheMode>enabled</PMKCacheMode>
			<PMKCacheTTL>720</PMKCacheTTL>
			<PMKCacheSize>128</PMKCacheSize>
			<preAuthThrottle>3</preAuthThrottle>
			<OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
				<maxAuthFailures>1</maxAuthFailures>
				<authMode>machine</authMode>
				<EAPConfig>
				<EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
				<EapMethod>
				<Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type> //TLS
				<VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
				<VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
				<AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
				</EapMethod>
				<Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
				<Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
				<Type>13</Type>
				<EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
				<CredentialsSource>
				<CertificateStore>
				<SimpleCertSelection>true</SimpleCertSelection>
				</CertificateStore>
				</CredentialsSource>
				<ServerValidation>
				<DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
				<ServerNames></ServerNames>
				<TrustedRootCA>xx xx xx xx xx xx xx xx xx xx xx xx xx xx xx xx xx xx xx xx </TrustedRootCA>
				</ServerValidation>
				<DifferentUsername>false</DifferentUsername>
				<PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">true</PerformServerValidation>
				<AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
				</EapType></Eap></Config></EapHostConfig></EAPConfig>
			</OneX>
		</security>
	</MSM>
</WLANProfile>

```

Some things are censored because i don't want to be identified :)

As far as i got:
Exported the certificate
Found out it uses TLS + 802.1X

Thanks in advance!
Aragagg

---

### Post by howefield on 2012-02-28
Speak to your schools IT administrator.

Thread closed.

---

