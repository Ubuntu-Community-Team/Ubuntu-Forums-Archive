---
title: "Patched network-manager-openvpn package for float option"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by onemyndseye on 2009-08-27
I have patched the OpenVPN NetworkManager plugin (network-manager-openvpn) to included the sorely missing --float option based on the version in the PPA right now ([https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa))

If this is something that interest you, you may check it out here:

**package no longer offered:  Use patch below **

---

### Post by onemyndseye on 2009-08-28
Heres a Patch file...


nm-advoptions-float.patch
```

--- network-manager-openvpn-0.7.1~20090213+bzr14.orig/properties/auth-helpers.c
+++ network-manager-openvpn-0.7.1~20090213+bzr14/properties/auth-helpers.c
@@ -718,6 +718,7 @@
 static const char *advanced_keys[] = {
 	NM_OPENVPN_KEY_PORT,
 	NM_OPENVPN_KEY_COMP_LZO,
+	NM_OPENVPN_KEY_FLOAT,
 	NM_OPENVPN_KEY_TAP_DEV,
 	NM_OPENVPN_KEY_PROTO_TCP,
 	NM_OPENVPN_KEY_CIPHER,
@@ -1005,6 +1006,13 @@
 		gtk_toggle_button_set_active (GTK_TOGGLE_BUTTON (widget), TRUE);
 	}
 
+	value = g_hash_table_lookup (hash, NM_OPENVPN_KEY_FLOAT);
+	if (value && !strcmp (value, "yes")) {
+		widget = glade_xml_get_widget (xml, "float_checkbutton");
+		gtk_toggle_button_set_active (GTK_TOGGLE_BUTTON (widget), TRUE);
+	}
+
+
 	value = g_hash_table_lookup (hash, NM_OPENVPN_KEY_PROTO_TCP);
 	if (value && !strcmp (value, "yes")) {
 		widget = glade_xml_get_widget (xml, "tcp_checkbutton");
@@ -1112,6 +1120,10 @@
 	if (gtk_toggle_button_get_active (GTK_TOGGLE_BUTTON (widget)))
 		g_hash_table_insert (hash, g_strdup (NM_OPENVPN_KEY_COMP_LZO), g_strdup ("yes"));
 
+	widget = glade_xml_get_widget (xml, "float_checkbutton");
+	if (gtk_toggle_button_get_active (GTK_TOGGLE_BUTTON (widget)))
+		g_hash_table_insert (hash, g_strdup (NM_OPENVPN_KEY_FLOAT), g_strdup ("yes"));
+
 	widget = glade_xml_get_widget (xml, "tcp_checkbutton");
 	if (gtk_toggle_button_get_active (GTK_TOGGLE_BUTTON (widget)))
 		g_hash_table_insert (hash, g_strdup (NM_OPENVPN_KEY_PROTO_TCP), g_strdup ("yes"));
--- network-manager-openvpn-0.7.1~20090213+bzr14.orig/properties/nm-openvpn-dialog.glade
+++ network-manager-openvpn-0.7.1~20090213+bzr14/properties/nm-openvpn-dialog.glade
@@ -935,6 +935,20 @@
                     <property name="position">3</property>
                   </packing>
                 </child>
+                <child>
+                  <widget class="GtkCheckButton" id="float_checkbutton">
+                    <property name="visible">True</property>
+                    <property name="can_focus">True</property>
+                    <property name="label" translatable="no">Use the _Float option</property>
+                    <property name="use_underline">True</property>
+                    <property name="response_id">0</property>
+                    <property name="draw_indicator">True</property>
+                  </widget>
+                  <packing>
+                    <property name="expand">False</property>
+                    <property name="position">3</property>
+                  </packing>
+                </child>
               </widget>
             </child>
             <child>
--- network-manager-openvpn-0.7.1~20090213+bzr14.orig/src/nm-openvpn-service.h
+++ network-manager-openvpn-0.7.1~20090213+bzr14/src/nm-openvpn-service.h
@@ -43,6 +43,7 @@
 #define NM_OPENVPN_KEY_CERT "cert"
 #define NM_OPENVPN_KEY_CIPHER "cipher"
 #define NM_OPENVPN_KEY_COMP_LZO "comp-lzo"
+#define NM_OPENVPN_KEY_FLOAT "float"
 #define NM_OPENVPN_KEY_CONNECTION_TYPE "connection-type"
 #define NM_OPENVPN_KEY_TAP_DEV "tap-dev"
 #define NM_OPENVPN_KEY_KEY "key"
--- network-manager-openvpn-0.7.1~20090213+bzr14.orig/src/nm-openvpn-service.c
+++ network-manager-openvpn-0.7.1~20090213+bzr14/src/nm-openvpn-service.c
@@ -88,6 +88,7 @@
 	{ NM_OPENVPN_KEY_CERT,                 G_TYPE_STRING, 0, 0, FALSE },
 	{ NM_OPENVPN_KEY_CIPHER,               G_TYPE_STRING, 0, 0, FALSE },
 	{ NM_OPENVPN_KEY_COMP_LZO,             G_TYPE_BOOLEAN, 0, 0, FALSE },
+	{ NM_OPENVPN_KEY_FLOAT,                G_TYPE_BOOLEAN, 0, 0, FALSE },
 	{ NM_OPENVPN_KEY_CONNECTION_TYPE,      G_TYPE_STRING, 0, 0, FALSE },
 	{ NM_OPENVPN_KEY_TAP_DEV,              G_TYPE_BOOLEAN, 0, 0, FALSE },
 	{ NM_OPENVPN_KEY_KEY,                  G_TYPE_STRING, 0, 0, FALSE },
@@ -640,6 +641,10 @@
 	if (tmp && !strcmp (tmp, "yes"))
 		add_openvpn_arg (args, "--comp-lzo");
 
+	tmp = nm_setting_vpn_get_data_item (s_vpn, NM_OPENVPN_KEY_FLOAT);
+	if (tmp && !strcmp (tmp, "yes"))
+		add_openvpn_arg (args, "--float");
+
 	add_openvpn_arg (args, "--nobind");
 
 	/* Device, either tun or tap */

```


You can apply this patch to the source of the current jaunty network-manager-openvpn plugin as follows:
```

mkdir ~/build-tmp
cd ~/build-tmp
apt-get source network-manager-openvpn
cd ./network-manager-openvpn*
wget http://onemyndseye.doesntexist.com/onemyndseye-ppa/patches/nm-advoptions-float.patch -O ./debian/patches/nm-advoptions-float.patch
echo "nm-advoptions-float.patch" >>./debian/patches/series
sudo apt-get build-dep network-mananger-openvpn
sudo apt-get install libglade2-dev devscripts build-essential
sudo dpkg-buildpackage 

```


Process could differ abit from system to system but that should give you a good general idea


Hope this helps,
-onemyndseye

---

### Post by Pavel Piatruk on 2010-12-24
Hello! I've found that NM Openvpn plugin  doesn't properly import 'comp-lzo' setting from ovpn file.

---

