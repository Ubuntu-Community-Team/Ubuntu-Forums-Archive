---
title: "OpenVPN client not setting up"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by Eric Bauld on 2010-10-01
I am trying to connect to an existing VPN server that I have been using for years now. I am moving my develpment environment over to a Ubuntu box and I must have openvpn working in order to access SVN. It has been a few years since I have been setting up linux boxes. And networking is a soft spot for me. But

The server has been running without problem for a LONG time. A windows computer I have been using connects to it fine and I can access the network on this machine.
I am setting up a new computer, but when trying to connect openvpn starts the initialization sequence completes but I cannot ping the network I am trying to connect to.

I use a second VPN connection to connect to an alternative network and it works fine. The difference between these two is that the working vpn connection is a routed IP tunnel and the one that is not working is a bridged connection. 

The VPN that is working on this box brings up tun0 while the bridged connection connects but does not bring up a network tun device. The server logs look normal, it just looks like the client is not setting itself up to use the network once connected. (The key/cert pair work find when on a windows box) Just not on this new ubuntu build.

My current client config
> 
cert [email]eric@home.crt[/email]
key [email]eric@home.key[/email]
client
dev tap
;dev tun
proto tcp
remote myseveraddress.com 1194
resolv-retry infinite
nobind
ca [email]ca@home.crt[/email]
cipher DES-EDE3-CBC
comp-lzo
verb 4

The server is using tap, as well as the working windows client uses "dev tap"

Any help/ideas would be great. It has been a long time since I have been maintaining linux boxes but its coming back slowly. 

Do I have to bring a device up manually ? I feel like I am missing something simple here ? Or its way over my head now. 

 - Eric

---

### Post by dmizer on 2010-10-01
Have you tried connecting via command line? There will be lots of output that will help with troubleshooting. Something like the following:
```
sudo openvpn myseveraddress.com.ovpn
```

You'll need to have the config file, the ca certificate, the client certificate, and the key all in the same directory.

---

### Post by Eric Bauld on 2010-10-01
This has all been via command line. I was having problems with gadmin-openvpn-client so I dropped it a while ago. I could not get it working with the connection that works fine on command line. But that is a different problem.

The connection that is not working looks normal, the sequence completes it does not disconnect and reconnect. But it does not bring up any device to get an ip address from the server ? 

The certs are in the same dir as the config file I am specifying via command line. I enter my private key password it connects to the server finishes its everything appears to be working but does not bring up a tap device on the client ?

---

### Post by Eric Bauld on 2010-10-01
Output from the command line
> Fri Oct  1 09:18:15 2010 us=855556 Current Parameter Settings:
Fri Oct  1 09:18:15 2010 us=855686   config = 'home.conf.ovpn'
Fri Oct  1 09:18:15 2010 us=855706   mode = 0
Fri Oct  1 09:18:15 2010 us=855721   persist_config = DISABLED
Fri Oct  1 09:18:15 2010 us=855735   persist_mode = 1
Fri Oct  1 09:18:15 2010 us=855748   show_ciphers = DISABLED
Fri Oct  1 09:18:15 2010 us=855762   show_digests = DISABLED
Fri Oct  1 09:18:15 2010 us=855775   show_engines = DISABLED
Fri Oct  1 09:18:15 2010 us=855788   genkey = DISABLED
Fri Oct  1 09:18:15 2010 us=855802   key_pass_file = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=855815   show_tls_ciphers = DISABLED
Fri Oct  1 09:18:15 2010 us=855829 Connection profiles [default]:
Fri Oct  1 09:18:15 2010 us=855843   proto = tcp-client
Fri Oct  1 09:18:15 2010 us=855857   local = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=855871   local_port = 0
Fri Oct  1 09:18:15 2010 us=855884   remote = '**Server***.com'
Fri Oct  1 09:18:15 2010 us=855898   remote_port = 1194
Fri Oct  1 09:18:15 2010 us=855911   remote_float = DISABLED
Fri Oct  1 09:18:15 2010 us=855925   bind_defined = DISABLED
Fri Oct  1 09:18:15 2010 us=855938   bind_local = DISABLED
Fri Oct  1 09:18:15 2010 us=855952   connect_retry_seconds = 5
Fri Oct  1 09:18:15 2010 us=855965   connect_timeout = 10
Fri Oct  1 09:18:15 2010 us=855978   connect_retry_max = 0
Fri Oct  1 09:18:15 2010 us=855992   socks_proxy_server = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856005   socks_proxy_port = 0
Fri Oct  1 09:18:15 2010 us=856019   socks_proxy_retry = DISABLED
Fri Oct  1 09:18:15 2010 us=856035 Connection profiles END
Fri Oct  1 09:18:15 2010 us=856049   remote_random = DISABLED
Fri Oct  1 09:18:15 2010 us=856062   ipchange = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856076   dev = 'tap'
Fri Oct  1 09:18:15 2010 us=856089   dev_type = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856102   dev_node = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856116   lladdr = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856129   topology = 1
Fri Oct  1 09:18:15 2010 us=856142   tun_ipv6 = DISABLED
Fri Oct  1 09:18:15 2010 us=856156   ifconfig_local = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856169   ifconfig_remote_netmask = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856183   ifconfig_noexec = DISABLED
Fri Oct  1 09:18:15 2010 us=856196   ifconfig_nowarn = DISABLED
Fri Oct  1 09:18:15 2010 us=856210   shaper = 0
Fri Oct  1 09:18:15 2010 us=856223   tun_mtu = 1500
Fri Oct  1 09:18:15 2010 us=856236   tun_mtu_defined = ENABLED
Fri Oct  1 09:18:15 2010 us=856250   link_mtu = 1500
Fri Oct  1 09:18:15 2010 us=856263   link_mtu_defined = DISABLED
Fri Oct  1 09:18:15 2010 us=856277   tun_mtu_extra = 32
Fri Oct  1 09:18:15 2010 us=856290   tun_mtu_extra_defined = ENABLED
Fri Oct  1 09:18:15 2010 us=856304   fragment = 0
Fri Oct  1 09:18:15 2010 us=856317   mtu_discover_type = -1
Fri Oct  1 09:18:15 2010 us=856330   mtu_test = 0
Fri Oct  1 09:18:15 2010 us=856344   mlock = DISABLED
Fri Oct  1 09:18:15 2010 us=856357   keepalive_ping = 0
Fri Oct  1 09:18:15 2010 us=856371   keepalive_timeout = 0
Fri Oct  1 09:18:15 2010 us=856384   inactivity_timeout = 0
Fri Oct  1 09:18:15 2010 us=856397   ping_send_timeout = 0
Fri Oct  1 09:18:15 2010 us=856411   ping_rec_timeout = 0
Fri Oct  1 09:18:15 2010 us=856424   ping_rec_timeout_action = 0
Fri Oct  1 09:18:15 2010 us=856437   ping_timer_remote = DISABLED
Fri Oct  1 09:18:15 2010 us=856451   remap_sigusr1 = 0
Fri Oct  1 09:18:15 2010 us=856464   explicit_exit_notification = 0
Fri Oct  1 09:18:15 2010 us=856478   persist_tun = DISABLED
Fri Oct  1 09:18:15 2010 us=856491   persist_local_ip = DISABLED
Fri Oct  1 09:18:15 2010 us=856505   persist_remote_ip = DISABLED
Fri Oct  1 09:18:15 2010 us=856518   persist_key = DISABLED
Fri Oct  1 09:18:15 2010 us=856532   mssfix = 1450
Fri Oct  1 09:18:15 2010 us=856545   passtos = DISABLED
Fri Oct  1 09:18:15 2010 us=856558   resolve_retry_seconds = 1000000000
Fri Oct  1 09:18:15 2010 us=856572   username = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856585   groupname = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856599   chroot_dir = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856612   cd_dir = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856632   writepid = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856646   up_script = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856659   down_script = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856673   down_pre = DISABLED
Fri Oct  1 09:18:15 2010 us=856686   up_restart = DISABLED
Fri Oct  1 09:18:15 2010 us=856700   up_delay = DISABLED
Fri Oct  1 09:18:15 2010 us=856713   daemon = DISABLED
Fri Oct  1 09:18:15 2010 us=856726   inetd = 0
Fri Oct  1 09:18:15 2010 us=856740   log = DISABLED
Fri Oct  1 09:18:15 2010 us=856753   suppress_timestamps = DISABLED
Fri Oct  1 09:18:15 2010 us=856767   nice = 0
Fri Oct  1 09:18:15 2010 us=856780   verbosity = 4
Fri Oct  1 09:18:15 2010 us=856794   mute = 0
Fri Oct  1 09:18:15 2010 us=856807   gremlin = 0
Fri Oct  1 09:18:15 2010 us=856821   status_file = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856834   status_file_version = 1
Fri Oct  1 09:18:15 2010 us=856848   status_file_update_freq = 60
Fri Oct  1 09:18:15 2010 us=856861   occ = ENABLED
Fri Oct  1 09:18:15 2010 us=856875   rcvbuf = 65536
Fri Oct  1 09:18:15 2010 us=856888   sndbuf = 65536
Fri Oct  1 09:18:15 2010 us=856901   sockflags = 0
Fri Oct  1 09:18:15 2010 us=856915   fast_io = DISABLED
Fri Oct  1 09:18:15 2010 us=856928   lzo = 7
Fri Oct  1 09:18:15 2010 us=856942   route_script = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856955   route_default_gateway = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=856969   route_default_metric = 0
Fri Oct  1 09:18:15 2010 us=856982   route_noexec = DISABLED
Fri Oct  1 09:18:15 2010 us=856996   route_delay = 0
Fri Oct  1 09:18:15 2010 us=857009   route_delay_window = 30
Fri Oct  1 09:18:15 2010 us=857023   route_delay_defined = DISABLED
Fri Oct  1 09:18:15 2010 us=857036   route_nopull = DISABLED
Fri Oct  1 09:18:15 2010 us=857050   route_gateway_via_dhcp = DISABLED
Fri Oct  1 09:18:15 2010 us=857064   max_routes = 100
Fri Oct  1 09:18:15 2010 us=857077   allow_pull_fqdn = DISABLED
Fri Oct  1 09:18:15 2010 us=857097   management_addr = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857112   management_port = 0
Fri Oct  1 09:18:15 2010 us=857125   management_user_pass = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857139   management_log_history_cache = 250
Fri Oct  1 09:18:15 2010 us=857152   management_echo_buffer_size = 100
Fri Oct  1 09:18:15 2010 us=857166   management_write_peer_info_file = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857180   management_client_user = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857193   management_client_group = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857207   management_flags = 0
Fri Oct  1 09:18:15 2010 us=857221   shared_secret_file = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857234   key_direction = 0
Fri Oct  1 09:18:15 2010 us=857248   ciphername_defined = ENABLED
Fri Oct  1 09:18:15 2010 us=857262   ciphername = 'DES-EDE3-CBC'
Fri Oct  1 09:18:15 2010 us=857275   authname_defined = ENABLED
Fri Oct  1 09:18:15 2010 us=857289   authname = 'SHA1'
Fri Oct  1 09:18:15 2010 us=857302   prng_hash = 'SHA1'
Fri Oct  1 09:18:15 2010 us=857316   prng_nonce_secret_len = 16
Fri Oct  1 09:18:15 2010 us=857329   keysize = 0
Fri Oct  1 09:18:15 2010 us=857343   engine = DISABLED
Fri Oct  1 09:18:15 2010 us=857357   replay = ENABLED
Fri Oct  1 09:18:15 2010 us=857370   mute_replay_warnings = DISABLED
Fri Oct  1 09:18:15 2010 us=857384   replay_window = 64
Fri Oct  1 09:18:15 2010 us=857398   replay_time = 15
Fri Oct  1 09:18:15 2010 us=857411   packet_id_file = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857425   use_iv = ENABLED
Fri Oct  1 09:18:15 2010 us=857438   test_crypto = DISABLED
Fri Oct  1 09:18:15 2010 us=857452   tls_server = DISABLED
Fri Oct  1 09:18:15 2010 us=857466   tls_client = ENABLED
Fri Oct  1 09:18:15 2010 us=857479   key_method = 2
Fri Oct  1 09:18:15 2010 us=857493   ca_file = 'ca@home.crt'
Fri Oct  1 09:18:15 2010 us=857507   ca_path = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857520   dh_file = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857534   cert_file = 'eric@home.crt'
Fri Oct  1 09:18:15 2010 us=857547   priv_key_file = 'eric@home.key'
Fri Oct  1 09:18:15 2010 us=857569   pkcs12_file = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857583   cipher_list = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857597   tls_verify = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857610   tls_remote = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857624   crl_file = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857637   ns_cert_type = 0
Fri Oct  1 09:18:15 2010 us=857651   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857665   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857678   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857692   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857705   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857719   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857732   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857746   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857759   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857773   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857786   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857799   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857813   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857826   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857840   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857854   remote_cert_ku[i] = 0
Fri Oct  1 09:18:15 2010 us=857868   remote_cert_eku = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=857882   tls_timeout = 2
Fri Oct  1 09:18:15 2010 us=857895   renegotiate_bytes = 0
Fri Oct  1 09:18:15 2010 us=857909   renegotiate_packets = 0
Fri Oct  1 09:18:15 2010 us=857923   renegotiate_seconds = 3600
Fri Oct  1 09:18:15 2010 us=857937   handshake_window = 60
Fri Oct  1 09:18:15 2010 us=857950   transition_window = 3600
Fri Oct  1 09:18:15 2010 us=857964   single_session = DISABLED
Fri Oct  1 09:18:15 2010 us=857977   tls_exit = DISABLED
Fri Oct  1 09:18:15 2010 us=857991   tls_auth_file = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=858005   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858019   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858032   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858046   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858060   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858073   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858087   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858101   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858115   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858128   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858142   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858156   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858170   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858184   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858197   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858211   pkcs11_protected_authentication = DISABLED
Fri Oct  1 09:18:15 2010 us=858226   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858240   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858254   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858268   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858282   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858296   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858309   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858323   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858337   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858351   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858365   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858379   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858392   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858406   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858429   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858443   pkcs11_private_mode = 00000000
Fri Oct  1 09:18:15 2010 us=858457   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858471   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858484   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858498   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858512   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858525   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858539   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858553   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858567   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858580   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858594   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858608   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858621   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858635   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858649   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858662   pkcs11_cert_private = DISABLED
Fri Oct  1 09:18:15 2010 us=858676   pkcs11_pin_cache_period = -1
Fri Oct  1 09:18:15 2010 us=858690   pkcs11_id = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=858704   pkcs11_id_management = DISABLED
Fri Oct  1 09:18:15 2010 us=858727   server_network = 0.0.0.0
Fri Oct  1 09:18:15 2010 us=858744   server_netmask = 0.0.0.0
Fri Oct  1 09:18:15 2010 us=858758   server_bridge_ip = 0.0.0.0
Fri Oct  1 09:18:15 2010 us=858774   server_bridge_netmask = 0.0.0.0
Fri Oct  1 09:18:15 2010 us=858788   server_bridge_pool_start = 0.0.0.0
Fri Oct  1 09:18:15 2010 us=858803   server_bridge_pool_end = 0.0.0.0
Fri Oct  1 09:18:15 2010 us=858817   ifconfig_pool_defined = DISABLED
Fri Oct  1 09:18:15 2010 us=858832   ifconfig_pool_start = 0.0.0.0
Fri Oct  1 09:18:15 2010 us=858847   ifconfig_pool_end = 0.0.0.0
Fri Oct  1 09:18:15 2010 us=858863   ifconfig_pool_netmask = 0.0.0.0
Fri Oct  1 09:18:15 2010 us=858876   ifconfig_pool_persist_filename = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=858890   ifconfig_pool_persist_refresh_freq = 600
Fri Oct  1 09:18:15 2010 us=858904   n_bcast_buf = 256
Fri Oct  1 09:18:15 2010 us=858918   tcp_queue_limit = 64
Fri Oct  1 09:18:15 2010 us=858932   real_hash_size = 256
Fri Oct  1 09:18:15 2010 us=858946   virtual_hash_size = 256
Fri Oct  1 09:18:15 2010 us=858959   client_connect_script = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=858973   learn_address_script = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=858987   client_disconnect_script = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=859001   client_config_dir = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=859015   ccd_exclusive = DISABLED
Fri Oct  1 09:18:15 2010 us=859028   tmp_dir = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=859042   push_ifconfig_defined = DISABLED
Fri Oct  1 09:18:15 2010 us=859057   push_ifconfig_local = 0.0.0.0
Fri Oct  1 09:18:15 2010 us=859079   push_ifconfig_remote_netmask = 0.0.0.0
Fri Oct  1 09:18:15 2010 us=859094   enable_c2c = DISABLED
Fri Oct  1 09:18:15 2010 us=859108   duplicate_cn = DISABLED
Fri Oct  1 09:18:15 2010 us=859121   cf_max = 0
Fri Oct  1 09:18:15 2010 us=859135   cf_per = 0
Fri Oct  1 09:18:15 2010 us=859149   max_clients = 1024
Fri Oct  1 09:18:15 2010 us=859163   max_routes_per_client = 256
Fri Oct  1 09:18:15 2010 us=859176   auth_user_pass_verify_script = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=859190   auth_user_pass_verify_script_via_file = DISABLED
Fri Oct  1 09:18:15 2010 us=859204   ssl_flags = 0
Fri Oct  1 09:18:15 2010 us=859218   port_share_host = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=859232   port_share_port = 0
Fri Oct  1 09:18:15 2010 us=859245   client = ENABLED
Fri Oct  1 09:18:15 2010 us=859259   pull = ENABLED
Fri Oct  1 09:18:15 2010 us=859273   auth_user_pass_file = '[UNDEF]'
Fri Oct  1 09:18:15 2010 us=859291 OpenVPN 2.1.0 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Fri Oct  1 09:18:15 2010 us=859412 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Fri Oct  1 09:18:15 2010 us=859428 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Fri Oct  1 09:18:18 2010 us=527183 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Fri Oct  1 09:18:18 2010 us=527391 WARNING: file 'eric@home.key' is group or others accessible
Fri Oct  1 09:18:18 2010 us=527958 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Fri Oct  1 09:18:18 2010 us=691261 LZO compression initialized
Fri Oct  1 09:18:18 2010 us=691472 Control Channel MTU parms [ L:1576 D:140 EF:40 EB:0 ET:0 EL:0 ]
Fri Oct  1 09:18:18 2010 us=819907 Data Channel MTU parms [ L:1576 D:1450 EF:44 EB:135 ET:32 EL:0 AF:3/1 ]
Fri Oct  1 09:18:18 2010 us=819970 Local Options String: 'V4,dev-type tap,link-mtu 1576,tun-mtu 1532,proto TCPv4_CLIENT,comp-lzo,cipher DES-EDE3-CBC,auth SHA1,keysize 192,key-method 2,tls-client'
Fri Oct  1 09:18:18 2010 us=819984 Expected Remote Options String: 'V4,dev-type tap,link-mtu 1576,tun-mtu 1532,proto TCPv4_SERVER,comp-lzo,cipher DES-EDE3-CBC,auth SHA1,keysize 192,key-method 2,tls-server'
Fri Oct  1 09:18:18 2010 us=820017 Local Options hash (VER=V4): '1a40e822'
Fri Oct  1 09:18:18 2010 us=820039 Expected Remote Options hash (VER=V4): 'd8e6e8ce'
Fri Oct  1 09:18:18 2010 us=820081 Attempting to establish TCP connection with [AF_INET]24.70.3.34:1194 [nonblock]
Fri Oct  1 09:18:19 2010 us=820237 TCP connection established with [AF_INET]24.70.3.34:1194
Fri Oct  1 09:18:19 2010 us=820316 Socket Buffers: R=[87380->131072] S=[16384->131072]
Fri Oct  1 09:18:19 2010 us=820338 TCPv4_CLIENT link local: [undef]
Fri Oct  1 09:18:19 2010 us=820355 TCPv4_CLIENT link remote: [AF_INET]***ipaddress***:1194
Fri Oct  1 09:18:19 2010 us=820676 TLS: Initial packet from [AF_INET]***ipaddress***:1194, sid=267f9053 b025b447
Fri Oct  1 09:18:20 2010 us=413000 VERIFY OK: depth=1, /C=CA/ST=***Province***/L=***City***/O=***Server***.com/CN=***server***.com/emailAddress=email@server.com
Fri Oct  1 09:18:20 2010 us=413361 VERIFY OK: depth=0, /C=CA/ST=***Province***/O=***Server***.com/CN=marvin/emailAddress=email@server.com
Fri Oct  1 09:18:21 2010 us=469322 Data Channel Encrypt: Cipher 'DES-EDE3-CBC' initialized with 192 bit key
Fri Oct  1 09:18:21 2010 us=469393 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Oct  1 09:18:21 2010 us=469412 Data Channel Decrypt: Cipher 'DES-EDE3-CBC' initialized with 192 bit key
Fri Oct  1 09:18:21 2010 us=469429 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Oct  1 09:18:21 2010 us=469488 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Fri Oct  1 09:18:21 2010 us=469524 [marvin] Peer Connection Initiated with [AF_INET]***ipaddress***:1194
Fri Oct  1 09:18:23 2010 us=816885 SENT CONTROL [marvin]: 'PUSH_REQUEST' (status=1)
Fri Oct  1 09:18:23 2010 us=965234 PUSH: Received control message: 'PUSH_REPLY,ping 10,ping-restart 60'
Fri Oct  1 09:18:23 2010 us=965302 OPTIONS IMPORT: timers and/or timeouts modified
Fri Oct  1 09:18:23 2010 us=966033 TUN/TAP device tap0 opened
Fri Oct  1 09:18:23 2010 us=966067 TUN/TAP TX queue length set to 100
Fri Oct  1 09:18:23 2010 us=966118 Initialization Sequence Completed

---

### Post by dmizer on 2010-10-01
You should go through that output and sanitize it.

Looks like everything finished correctly with a tap device configured. FYI, after running the openvpn connection command, the terminal will not return you to a prompt.

---

### Post by Eric Bauld on 2010-10-01
Sanitized... I think

That is what confuses me. Openvpn starts and looks good. Once that is complete I cannot ping the vpn server. And there are no additional tap devices setup (as per ifconfig), thus it cannot receive an ip address. As far as openvpn is concerned it is working fine. But it does not actually bring up a tap device on this connection. 

But my other vpn connection works fine.

---

### Post by dmizer on 2010-10-01
Not too sure what to tell you from here then. It looks good to me. The conf file looks correct and the openvpn output looks good and complete. You are running openvpn as root (sudo), correct?

Only other thing I can think of to suggest before I crash for the night is to try asking in IRC at #openvpn

---

