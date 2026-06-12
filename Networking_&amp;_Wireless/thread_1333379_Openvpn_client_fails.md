---
title: "Openvpn client fails"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by blwegrzyn on 2009-11-21
Hello, when i try to use openvpn as client in ubuntu in tap mode the connection fails.  Below is the log and server and client configs:

log:
blwegrzyn@blwegrzyn-laptop:~/openvpn$ sudo openvpn vpn
Sat Nov 21 10:36:46 2009 us=478033 Current Parameter Settings:
Sat Nov 21 10:36:46 2009 us=478225   config = 'vpn'
Sat Nov 21 10:36:46 2009 us=478260   mode = 0
Sat Nov 21 10:36:46 2009 us=478289   persist_config = DISABLED
Sat Nov 21 10:36:46 2009 us=478317   persist_mode = 1
Sat Nov 21 10:36:46 2009 us=478344   show_ciphers = DISABLED
Sat Nov 21 10:36:46 2009 us=478372   show_digests = DISABLED
Sat Nov 21 10:36:46 2009 us=478399   show_engines = DISABLED
Sat Nov 21 10:36:46 2009 us=478427   genkey = DISABLED
Sat Nov 21 10:36:46 2009 us=478454   key_pass_file = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=478482   show_tls_ciphers = DISABLED
Sat Nov 21 10:36:46 2009 us=478513 Connection profiles [default]:
Sat Nov 21 10:36:46 2009 us=478543   proto = udp
Sat Nov 21 10:36:46 2009 us=478570   local = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=478597   local_port = 0
Sat Nov 21 10:36:46 2009 us=478624   remote = 'xxx.com'
Sat Nov 21 10:36:46 2009 us=478652   remote_port = 1194
Sat Nov 21 10:36:46 2009 us=478678   remote_float = DISABLED
Sat Nov 21 10:36:46 2009 us=478705   bind_defined = DISABLED
Sat Nov 21 10:36:46 2009 us=478732   bind_local = DISABLED
Sat Nov 21 10:36:46 2009 us=478759   connect_retry_seconds = 5
Sat Nov 21 10:36:46 2009 us=478787   connect_timeout = 10
Sat Nov 21 10:36:46 2009 us=478814   connect_retry_max = 0
Sat Nov 21 10:36:46 2009 us=478840   socks_proxy_server = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=478868   socks_proxy_port = 0
Sat Nov 21 10:36:46 2009 us=478894   socks_proxy_retry = DISABLED
Sat Nov 21 10:36:46 2009 us=478925 Connection profiles END
Sat Nov 21 10:36:46 2009 us=478953   remote_random = DISABLED
Sat Nov 21 10:36:46 2009 us=478980   ipchange = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=479006   dev = 'tap1'
Sat Nov 21 10:36:46 2009 us=479032   dev_type = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=479058   dev_node = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=479084   lladdr = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=479110   topology = 1
Sat Nov 21 10:36:46 2009 us=479136   tun_ipv6 = DISABLED
Sat Nov 21 10:36:46 2009 us=479162   ifconfig_local = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=479189   ifconfig_remote_netmask = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=479216   ifconfig_noexec = DISABLED
Sat Nov 21 10:36:46 2009 us=479243   ifconfig_nowarn = DISABLED
Sat Nov 21 10:36:46 2009 us=479270   shaper = 0
Sat Nov 21 10:36:46 2009 us=479296   tun_mtu = 1500
Sat Nov 21 10:36:46 2009 us=479322   tun_mtu_defined = ENABLED
Sat Nov 21 10:36:46 2009 us=479348   link_mtu = 1500
Sat Nov 21 10:36:46 2009 us=479375   link_mtu_defined = DISABLED
Sat Nov 21 10:36:46 2009 us=479401   tun_mtu_extra = 32
Sat Nov 21 10:36:46 2009 us=479428   tun_mtu_extra_defined = ENABLED
Sat Nov 21 10:36:46 2009 us=479455   fragment = 0
Sat Nov 21 10:36:46 2009 us=479481   mtu_discover_type = -1
Sat Nov 21 10:36:46 2009 us=479508   mtu_test = 0
Sat Nov 21 10:36:46 2009 us=479533   mlock = DISABLED
Sat Nov 21 10:36:46 2009 us=479560   keepalive_ping = 0
Sat Nov 21 10:36:46 2009 us=479587   keepalive_timeout = 0
Sat Nov 21 10:36:46 2009 us=479613   inactivity_timeout = 0
Sat Nov 21 10:36:46 2009 us=479639   ping_send_timeout = 0
Sat Nov 21 10:36:46 2009 us=479665   ping_rec_timeout = 0
Sat Nov 21 10:36:46 2009 us=479691   ping_rec_timeout_action = 0
Sat Nov 21 10:36:46 2009 us=479717   ping_timer_remote = DISABLED
Sat Nov 21 10:36:46 2009 us=479743   remap_sigusr1 = 0
Sat Nov 21 10:36:46 2009 us=479770   explicit_exit_notification = 0
Sat Nov 21 10:36:46 2009 us=479796   persist_tun = ENABLED
Sat Nov 21 10:36:46 2009 us=479823   persist_local_ip = DISABLED
Sat Nov 21 10:36:46 2009 us=479849   persist_remote_ip = DISABLED
Sat Nov 21 10:36:46 2009 us=479876   persist_key = ENABLED
Sat Nov 21 10:36:46 2009 us=479903   mssfix = 1450
Sat Nov 21 10:36:46 2009 us=479928   passtos = DISABLED
Sat Nov 21 10:36:46 2009 us=479955   resolve_retry_seconds = 1000000000
Sat Nov 21 10:36:46 2009 us=479982   username = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=480009   groupname = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=480035   chroot_dir = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=480062   cd_dir = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=480089   writepid = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=480115   up_script = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=480142   down_script = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=480168   down_pre = DISABLED
Sat Nov 21 10:36:46 2009 us=480195   up_restart = DISABLED
Sat Nov 21 10:36:46 2009 us=480222   up_delay = DISABLED
Sat Nov 21 10:36:46 2009 us=480248   daemon = DISABLED
Sat Nov 21 10:36:46 2009 us=480274   inetd = 0
Sat Nov 21 10:36:46 2009 us=480301   log = DISABLED
Sat Nov 21 10:36:46 2009 us=480327   suppress_timestamps = DISABLED
Sat Nov 21 10:36:46 2009 us=480353   nice = 0
Sat Nov 21 10:36:46 2009 us=480379   verbosity = 5
Sat Nov 21 10:36:46 2009 us=480406   mute = 0
Sat Nov 21 10:36:46 2009 us=480433   gremlin = 0
Sat Nov 21 10:36:46 2009 us=480458   status_file = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=480485   status_file_version = 1
Sat Nov 21 10:36:46 2009 us=480512   status_file_update_freq = 60
Sat Nov 21 10:36:46 2009 us=480538   occ = ENABLED
Sat Nov 21 10:36:46 2009 us=480564   rcvbuf = 65536
Sat Nov 21 10:36:46 2009 us=480590   sndbuf = 65536
Sat Nov 21 10:36:46 2009 us=480617   sockflags = 0
Sat Nov 21 10:36:46 2009 us=480643   fast_io = DISABLED
Sat Nov 21 10:36:46 2009 us=480669   lzo = 7
Sat Nov 21 10:36:46 2009 us=480695   route_script = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=480722   route_default_gateway = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=480749   route_default_metric = 0
Sat Nov 21 10:36:46 2009 us=480775   route_noexec = DISABLED
Sat Nov 21 10:36:46 2009 us=480804   route_delay = 0
Sat Nov 21 10:36:46 2009 us=480830   route_delay_window = 30
Sat Nov 21 10:36:46 2009 us=480857   route_delay_defined = DISABLED
Sat Nov 21 10:36:46 2009 us=480884   route_nopull = DISABLED
Sat Nov 21 10:36:46 2009 us=480911   route_gateway_via_dhcp = DISABLED
Sat Nov 21 10:36:46 2009 us=480939   allow_pull_fqdn = DISABLED
Sat Nov 21 10:36:46 2009 us=480966   management_addr = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=480994   management_port = 0
Sat Nov 21 10:36:46 2009 us=481021   management_user_pass = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=481049   management_log_history_cache = 250
Sat Nov 21 10:36:46 2009 us=481076   management_echo_buffer_size = 100
Sat Nov 21 10:36:46 2009 us=481104   management_write_peer_info_file = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=481132   management_client_user = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=481160   management_client_group = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=481188   management_flags = 0
Sat Nov 21 10:36:46 2009 us=481215   shared_secret_file = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=481242   key_direction = 0
Sat Nov 21 10:36:46 2009 us=481269   ciphername_defined = ENABLED
Sat Nov 21 10:36:46 2009 us=481297   ciphername = 'BF-CBC'
Sat Nov 21 10:36:46 2009 us=481323   authname_defined = ENABLED
Sat Nov 21 10:36:46 2009 us=488910   authname = 'SHA1'
Sat Nov 21 10:36:46 2009 us=488961   prng_hash = 'SHA1'
Sat Nov 21 10:36:46 2009 us=488989   prng_nonce_secret_len = 16
Sat Nov 21 10:36:46 2009 us=489016   keysize = 0
Sat Nov 21 10:36:46 2009 us=489043   engine = DISABLED
Sat Nov 21 10:36:46 2009 us=489070   replay = ENABLED
Sat Nov 21 10:36:46 2009 us=489097   mute_replay_warnings = DISABLED
Sat Nov 21 10:36:46 2009 us=489124   replay_window = 64
Sat Nov 21 10:36:46 2009 us=489151   replay_time = 15
Sat Nov 21 10:36:46 2009 us=489177   packet_id_file = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=489204   use_iv = ENABLED
Sat Nov 21 10:36:46 2009 us=489231   test_crypto = DISABLED
Sat Nov 21 10:36:46 2009 us=489257   tls_server = DISABLED
Sat Nov 21 10:36:46 2009 us=489283   tls_client = ENABLED
Sat Nov 21 10:36:46 2009 us=489308   key_method = 2
Sat Nov 21 10:36:46 2009 us=489335   ca_file = '/home/blwegrzyn/openvpn/ca.crt'
Sat Nov 21 10:36:46 2009 us=489363   ca_path = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=489389   dh_file = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=489416   cert_file = '/home/blwegrzyn/openvpn/client1.crt'
Sat Nov 21 10:36:46 2009 us=489443   priv_key_file = '/home/blwegrzyn/openvpn/client1.key'
Sat Nov 21 10:36:46 2009 us=489470   pkcs12_file = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=489497   cipher_list = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=489523   tls_verify = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=489549   tls_remote = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=489576   crl_file = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=489602   ns_cert_type = 0
Sat Nov 21 10:36:46 2009 us=489629   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489656   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489682   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489708   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489734   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489760   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489786   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489811   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489837   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489863   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489889   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489914   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489940   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489966   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=489992   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=490018   remote_cert_ku[i] = 0
Sat Nov 21 10:36:46 2009 us=490045   remote_cert_eku = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=490072   tls_timeout = 2
Sat Nov 21 10:36:46 2009 us=490098   renegotiate_bytes = 0
Sat Nov 21 10:36:46 2009 us=490123   renegotiate_packets = 0
Sat Nov 21 10:36:46 2009 us=490150   renegotiate_seconds = 3600
Sat Nov 21 10:36:46 2009 us=490176   handshake_window = 60
Sat Nov 21 10:36:46 2009 us=490202   transition_window = 3600
Sat Nov 21 10:36:46 2009 us=490229   single_session = DISABLED
Sat Nov 21 10:36:46 2009 us=490256   tls_exit = DISABLED
Sat Nov 21 10:36:46 2009 us=490284   tls_auth_file = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=490312   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490340   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490367   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490394   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490421   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490461   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490493   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490521   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490548   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490575   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490602   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490630   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490657   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490684   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490711   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490738   pkcs11_protected_authentication = DISABLED
Sat Nov 21 10:36:46 2009 us=490766   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=490793   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=490820   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=490847   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=490874   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=490901   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=490928   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=490955   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=490982   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=491009   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=491036   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=491062   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=491089   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=491116   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=491143   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=491170   pkcs11_private_mode = 00000000
Sat Nov 21 10:36:46 2009 us=491196   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491223   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491251   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491277   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491304   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491330   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491357   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491384   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491410   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491437   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491463   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491490   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491516   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491543   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491569   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491595   pkcs11_cert_private = DISABLED
Sat Nov 21 10:36:46 2009 us=491623   pkcs11_pin_cache_period = -1
Sat Nov 21 10:36:46 2009 us=491649   pkcs11_id = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=491676   pkcs11_id_management = DISABLED
Sat Nov 21 10:36:46 2009 us=491737   server_network = 0.0.0.0
Sat Nov 21 10:36:46 2009 us=498752   server_netmask = 0.0.0.0
Sat Nov 21 10:36:46 2009 us=498792   server_bridge_ip = 0.0.0.0
Sat Nov 21 10:36:46 2009 us=498823   server_bridge_netmask = 0.0.0.0
Sat Nov 21 10:36:46 2009 us=498853   server_bridge_pool_start = 0.0.0.0
Sat Nov 21 10:36:46 2009 us=498883   server_bridge_pool_end = 0.0.0.0
Sat Nov 21 10:36:46 2009 us=498911   ifconfig_pool_defined = DISABLED
Sat Nov 21 10:36:46 2009 us=498942   ifconfig_pool_start = 0.0.0.0
Sat Nov 21 10:36:46 2009 us=498971   ifconfig_pool_end = 0.0.0.0
Sat Nov 21 10:36:46 2009 us=499000   ifconfig_pool_netmask = 0.0.0.0
Sat Nov 21 10:36:46 2009 us=499028   ifconfig_pool_persist_filename = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=499057   ifconfig_pool_persist_refresh_freq = 600
Sat Nov 21 10:36:46 2009 us=499085   n_bcast_buf = 256
Sat Nov 21 10:36:46 2009 us=499113   tcp_queue_limit = 64
Sat Nov 21 10:36:46 2009 us=499140   real_hash_size = 256
Sat Nov 21 10:36:46 2009 us=499167   virtual_hash_size = 256
Sat Nov 21 10:36:46 2009 us=499195   client_connect_script = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=499223   learn_address_script = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=499251   client_disconnect_script = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=499279   client_config_dir = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=499306   ccd_exclusive = DISABLED
Sat Nov 21 10:36:46 2009 us=499333   tmp_dir = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=499360   push_ifconfig_defined = DISABLED
Sat Nov 21 10:36:46 2009 us=499391   push_ifconfig_local = 0.0.0.0
Sat Nov 21 10:36:46 2009 us=499421   push_ifconfig_remote_netmask = 0.0.0.0
Sat Nov 21 10:36:46 2009 us=499448   enable_c2c = DISABLED
Sat Nov 21 10:36:46 2009 us=499476   duplicate_cn = DISABLED
Sat Nov 21 10:36:46 2009 us=499503   cf_max = 0
Sat Nov 21 10:36:46 2009 us=499530   cf_per = 0
Sat Nov 21 10:36:46 2009 us=499557   max_clients = 1024
Sat Nov 21 10:36:46 2009 us=499585   max_routes_per_client = 256
Sat Nov 21 10:36:46 2009 us=499612   auth_user_pass_verify_script = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=499641   auth_user_pass_verify_script_via_file = DISABLED
Sat Nov 21 10:36:46 2009 us=499669   ssl_flags = 0
Sat Nov 21 10:36:46 2009 us=499696   port_share_host = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=499724   port_share_port = 0
Sat Nov 21 10:36:46 2009 us=499750   client = ENABLED
Sat Nov 21 10:36:46 2009 us=499777   pull = ENABLED
Sat Nov 21 10:36:46 2009 us=499804   auth_user_pass_file = '[UNDEF]'
Sat Nov 21 10:36:46 2009 us=499842 OpenVPN 2.1_rc19 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Sat Nov 21 10:36:46 2009 us=500092 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Sat Nov 21 10:36:46 2009 us=500125 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sat Nov 21 10:36:46 2009 us=501927 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Sat Nov 21 10:36:46 2009 us=624494 LZO compression initialized
Sat Nov 21 10:36:46 2009 us=624632 Control Channel MTU parms [ L:1574 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sat Nov 21 10:36:46 2009 us=625695 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Sat Nov 21 10:36:46 2009 us=625750 Local Options String: 'V4,dev-type tap,link-mtu 1574,tun-mtu 1532,proto UDPv4,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,key-method 2,tls-client'
Sat Nov 21 10:36:46 2009 us=625773 Expected Remote Options String: 'V4,dev-type tap,link-mtu 1574,tun-mtu 1532,proto UDPv4,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,key-method 2,tls-server'
Sat Nov 21 10:36:46 2009 us=625820 Local Options hash (VER=V4): 'd79ca330'
Sat Nov 21 10:36:46 2009 us=625849 Expected Remote Options hash (VER=V4): 'f7df56b8'
Sat Nov 21 10:36:46 2009 us=625885 Socket Buffers: R=[129024->131072] S=[129024->131072]
Sat Nov 21 10:36:46 2009 us=625910 UDPv4 link local: [undef]
Sat Nov 21 10:36:46 2009 us=625932 UDPv4 link remote: 99.177.129.250:1194
WRSat Nov 21 10:36:46 2009 us=666343 TLS: Initial packet from 99.177.129.250:1194, sid=499e9ed6 43f7a243
WWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRSat Nov 21 10:36:47 2009 us=79550 VERIFY OK: depth=1, /C=US/ST=IL/L=OAKPARK/O=OpenVPN-xxx/OU=CA/CN=xxx/emailAddress=openvpn@xxx
Sat Nov 21 10:36:47 2009 us=80058 VERIFY OK: depth=0, /C=US/ST=IL/O=OpenVPN-Lexoncom/OU=VPNServer/CN=vpn.lexoncom.com/emailAddress=openvpn@xxx
WRWRWRWRWRWRWWWWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRWRRRRWWWWRRRRWRWRSat Nov 21 10:36:47 2009 us=584990 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sat Nov 21 10:36:47 2009 us=585058 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sat Nov 21 10:36:47 2009 us=585232 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sat Nov 21 10:36:47 2009 us=585304 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
WSat Nov 21 10:36:47 2009 us=585431 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Sat Nov 21 10:36:47 2009 us=585495 [vpn.xxx.com] Peer Connection Initiated with 99.177.129.250:1194
RRRSat Nov 21 10:36:48 2009 us=100016 SENT CONTROL [vpn.xxx.com]: 'PUSH_REQUEST' (status=1)
WRRRWRSat Nov 21 10:36:48 2009 us=134125 PUSH: Received control message: 'PUSH_REPLY,route 192.168.1.0 255.255.255.0,redirect-gateway,dhcp-option DNS 192.168.1.241,route-gateway 192.168.1.254,ping 10,ping-restart 120'
Sat Nov 21 10:36:48 2009 us=134298 OPTIONS IMPORT: timers and/or timeouts modified
Sat Nov 21 10:36:48 2009 us=134331 OPTIONS IMPORT: route options modified
Sat Nov 21 10:36:48 2009 us=134356 OPTIONS IMPORT: route-related options modified
Sat Nov 21 10:36:48 2009 us=134380 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Sat Nov 21 10:36:48 2009 us=134675 ROUTE default_gateway=10.100.55.1
Sat Nov 21 10:36:48 2009 us=137352 TUN/TAP device tap1 opened
Sat Nov 21 10:36:48 2009 us=137409 TUN/TAP TX queue length set to 100
Sat Nov 21 10:36:48 2009 us=137518 /sbin/route add -net 99.177.129.250 netmask 255.255.255.255 gw 10.100.55.1
Sat Nov 21 10:36:48 2009 us=140104 /sbin/route del -net 0.0.0.0 netmask 0.0.0.0
Sat Nov 21 10:36:48 2009 us=146679 /sbin/route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.1.254
SIOCADDRT: No such process
Sat Nov 21 10:36:48 2009 us=149421 ERROR: Linux route add command failed: external program exited with error status: 7
Sat Nov 21 10:36:48 2009 us=149583 /sbin/route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.254
SIOCADDRT: No such process
Sat Nov 21 10:36:48 2009 us=150473 ERROR: Linux route add command failed: external program exited with error status: 7
Sat Nov 21 10:36:48 2009 us=150508 Initialization Sequence Completed


server config:

mode server
port 1194
proto udp
dev tap0
ca /etc/easy-rsa/keys/ca.crt
cert /etc/easy-rsa/keys/server.crt
key /etc/easy-rsa/keys/server.key  # This file should be kept secret
dh /etc/easy-rsa/keys/dh1024.pem
push "route 192.168.1.0 255.255.255.0"
push "redirect-gateway"
push "dhcp-option DNS 192.168.1.241"
push "route-gateway 192.168.1.254"
keepalive 10 120
route-gateway 192.168.1.254
comp-lzo
persist-key
persist-tun
status /etc/openvpn/openvpn-status.log
verb 3
tls-server
duplicate-cn

client config:
client
dev tap1
proto udp
remote xxx 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca /home/blwegrzyn/openvpn/ca.crt
cert /home/blwegrzyn/openvpn/client1.crt
key /home/blwegrzyn/openvpn/client1.key
comp-lzo
verb 3

---

