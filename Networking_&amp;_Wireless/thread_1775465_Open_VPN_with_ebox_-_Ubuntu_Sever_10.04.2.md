---
title: "Open VPN with ebox - Ubuntu Sever 10.04.2"
date: 2011-06-04
forum: Networking &amp; Wireless
---

### Post by Jonny87 on 2011-06-04
I was trying to set up a vpn through ebox and all was going fine untill I tried to download the client cert package. It spat out the following error.

> 
**A really nasty bug has occurred**

**Exception**

root command chmod 0600 /var/lib/ebox/tmp/downloads/Home Base-client.zip failed.  Error output: chmod: cannot access `/var/lib/ebox/tmp/downloads/Home': No such file or directory  chmod: cannot access `Base-client.zip': No such file or directory  Command output: .  Exit value: 1[B]

Trace[/B]

root command chmod 0600 /var/lib/ebox/tmp/downloads/Home Base-client.zip failed. 
Error output: chmod: cannot access `/var/lib/ebox/tmp/downloads/Home': No such file or directory
 chmod: cannot access `Base-client.zip': No such file or directory

Command output: . 
Exit value: 1 at /usr/share/perl5/Error.pm line 182
    Error::throw('EBox::Exceptions::Sudo::Command', 'cmd', 'chmod 0600  /var/lib/ebox/tmp/downloads/Home Base-client.zip', 'output',  'ARRAY(0xb9db48d0)', 'error', 'ARRAY(0xb9d83cb0)', 'exitValue', 1, ...)  called at /usr/share/perl5/EBox/Sudo.pm line 215
     EBox::Sudo::_rootError('/usr/bin/sudo -p sudo:  /var/lib/ebox/tmp/eXfbHC7cxO.cmd 2> /v...', 'chmod 0600  /var/lib/ebox/tmp/downloads/Home Base-client.zip', 256,  'ARRAY(0xb9db48d0)', 'ARRAY(0xb9d83cb0)') called at  /usr/share/perl5/EBox/Sudo.pm line 182
    EBox::Sudo::_root(1, 'chmod  0600 /var/lib/ebox/tmp/downloads/Home Base-client.zip') called at  /usr/share/perl5/EBox/Sudo.pm line 137
    EBox::Sudo::root('chmod 0600  /var/lib/ebox/tmp/downloads/Home Base-client.zip') called at  /usr/share/perl5/EBox/OpenVPN/Server/ClientBundleGenerator.pm line 256
     EBox::OpenVPN::Server::ClientBundleGenerator::_createBundle('EBox::OpenVPN::Server::ClientBundleGenerator::Windows',  'EBox::OpenVPN::Server=HASH(0xb9d82a48)', '/var/lib/ebox/tmp/Home  Base-client.tmp', 'installer', 'on', 'addresses', 'ARRAY(0xb9db4c20)',  'clientCertificate', 'TTVPN', ...) called at  /usr/share/perl5/EBox/OpenVPN/Server/ClientBundleGenerator.pm line 210
     EBox::OpenVPN::Server::ClientBundleGenerator::clientBundle('EBox::OpenVPN::Server::ClientBundleGenerator::Windows',  'installer', 'on', 'addresses', 'ARRAY(0xb9db4c20)',  'clientCertificate', 'TTVPN', 'server',  'EBox::OpenVPN::Server=HASH(0xb9d82a48)', ...) called at  /usr/share/perl5/EBox/OpenVPN/Server.pm line 517
     EBox::OpenVPN::Server::clientBundle('EBox::OpenVPN::Server=HASH(0xb9d82a48)',  'clientType', 'windows', 'clientCertificate', 'TTVPN', 'addresses',  'ARRAY(0xb9db4c20)', 'installer', 'on', ...) called at  /usr/share/perl5/EBox/OpenVPN/Model/DownloadClientBundle.pm line 275
     EBox::OpenVPN::Model::DownloadClientBundle::formSubmitted('EBox::OpenVPN::Model::DownloadClientBundle=HASH(0xb99fc530)',  'EBox::Model::Row=HASH(0xb9d60c40)', undef) called at  /usr/share/perl5/EBox/Model/DataForm.pm line 573
     EBox::Model::DataForm::updatedRowNotify('EBox::OpenVPN::Model::DownloadClientBundle=HASH(0xb99fc530)',  'EBox::Model::Row=HASH(0xb9d60c40)', undef) called at  /usr/share/perl5/EBox/Model/DataForm/Action.pm line 108
     EBox::Model::DataForm::Action::setTypedRow('EBox::OpenVPN::Model::DownloadClientBundle=HASH(0xb99fc530)',  '', 'HASH(0xb9c76048)', 'force', undef, 'readOnly', undef) called at  /usr/share/perl5/EBox/Model/DataForm.pm line 341
     EBox::Model::DataForm::setRow('EBox::OpenVPN::Model::DownloadClientBundle=HASH(0xb99fc530)',  undef, 'certificate', 'TTVPN', 'filter', '', 'clientType', 'windows',  'addr2', ...) called at  /usr/share/perl5/EBox/CGI/Controller/DataTable.pm line 121
     EBox::CGI::Controller::DataTable::editField('EBox::CGI::Controller::DataTable=HASH(0xb9d5de88)')  called at /usr/share/perl5/EBox/CGI/Controller/DataTable.pm line 226
     EBox::CGI::Controller::DataTable::_process('EBox::CGI::Controller::DataTable=HASH(0xb9d5de88)')  called at /usr/share/perl5/EBox/CGI/ClientRawBase.pm line 173
     EBox::CGI::ClientRawBase::run('EBox::CGI::Controller::DataTable=HASH(0xb9d5de88)')  called at /usr/share/perl5/EBox/CGI/Run.pm line 120
     EBox::CGI::Run::run('EBox::CGI::Run',  'OpenVPN/Controller/DownloadClientBundle', 'EBox') called at  /usr/share/ebox/cgi/ebox.cgi line 19
     ModPerl::ROOT::ModPerl::Registry::usr_share_ebox_cgi_ebox_2ecgi::handler('Apache2::RequestRec=SCALAR(0xb9d20c38)')  called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
    eval {...} called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 204
    ModPerl::RegistryCooker::run('ModPerl::Registry=HASH(0xb9c94b68)') called at /usr/lib/perl5/ModPerl/RegistryCooker.pm line 170
     ModPerl::RegistryCooker::default_handler('ModPerl::Registry=HASH(0xb9c94b68)')  called at /usr/lib/perl5/ModPerl/Registry.pm line 31
    ModPerl::Registry::handler('ModPerl::Registry', 'Apache2::RequestRec=SCALAR(0xb9d20c38)') called at -e line 0
    eval {...} called at -e line 0
I should probably mention that the server is running in virtual box. and the I'm accessing it from my real desktop web browser, if this is relevant at all.

Any help would be appreciated thanks.

---

