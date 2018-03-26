# hwconfig
For check a Hardware Spec. &amp; verify an environment by check-list

* Notice! Bin files for the RHEL Linux only if you need to use the hwconfig to the ubuntu, then you should install the lspci & MegaCli to the ubuntu by packages.

## How to install
```
sudo mkdir -p /data
sudo mv ./bin /data/
sudo chmod +x /data/bin/*
```

* Show up the HW Spec.
* $] hwconfig

```
Hostname: 	 manager01.ralfyang.com
Summary: 	 S210-X12RS, Intel(R) Xeon(R) CPU E5-2640 0 @ 2.50GHz x 12(Core), 56996580 / 65946184, 8192MB x 8ea, 2U
System: 	 S210-X12RS | Chassis: 2U
Processors: 	 Intel(R) Xeon(R) CPU E5-2640 0 @ 2.50GHz x 12(Core)
Memory: 	 56996580 / 65946184 (8192MB x 8ea)
Disk: 		 sda=1198.0GB mapper/VG_data-lv_data=1081.0GB
Storage: 	 Intel Corporation C602 chipset 4-Port SATA Storage Control Unit (rev 05)
RAID Level: 	 N/A
RAID Disks: 	 N/A
Network 0: 	 eth0=1.2.4.254 		 Netmask=255.255.255.0
Gateway: 	 1.2.4.1
OS: 		 CentOS release 6.4 (Final)
BIOS: 		 American Megatrends Inc. S2RQ3A19
HW Serial: 	 WDSCEV2270082
Kernel: 	 Linux 2.6.32-358.6.1.el6.x86_64 #1 SMP x86_64 - Apr/23/2013
PowerSupply: 	 2 onlined power cord(s)
```

* Show up the HW Spec. for crawling
* $] hwconfig -c
```
| Hostname: manager01.ralfyang.com | OS: CentOS release 6.4 (Final) | CPU: Intel(R) Xeon(R) CPU E5-2640 0 @ 2.50GHz x 12(Core) | System: S210-X12RS  | UnitSize: 2U | Memory: 65946184 (8192MB x 8ea) | Disk size: sda=1198.0GB mapper/VG_data-lv_data=1081.0GB | Disk Qtty.: N/A | Disk type:  | Storage: Intel Corporation C602 chipset 4-Port SATA Storage Control Unit (rev 05) | RAID: N/A | Owner:  | Group: | Property: | Service: | Int.Switch: | Ext.Switch: | Rack: | IDC: | Network 0: eth0 1.2.4.254 | Netmask 0: 255.255.255.0 | Network 1:   | Netmask 1:  | Gateway: 1.2.4.1 | RAC IP: | Serial: WDFCEV2270082  | BIOS: American Megatrends Inc. S2RQ3A19 | Enterd: | Kernel: Linux 2.6.32-358.6.1.el6.x86_64 #1 SMP x86_64 | Update: 2015-07-16| @END@
```

* Make a check-list by checklist.txt file
* $] hwconfig -check
```
======================================================================================================================
 Configuration                       Target                           Current                                Result
======================================================================================================================
 CentOS Version                      6.4                              Not exist                          Not ok - x
 Kernel Version                      2.6.32-358.el6.x86_64            2.6.32-358.6.1.el6.x86_64          Not ok - x
 Locale                              ko_KR.UTF-8                      ko_KR.UTF-8                            Ok - o
 Umask                               002                              002                                    Ok - o
 Ulimit                              8192                             1024                               Not ok - x
 Selinux                             disabled                         disabled                               Ok - o
 Init                                3                                3                                      Ok - o
 Service DIR                         applications                     applications                           Ok - o
 Service account                     service                          service                                Ok - o
 Monitoring account                  nagios                           nagios                                 Ok - o
 DNS-1st                             8.8.8.8                          8.8.8.8                                Ok - o
 DNS-2nd                             168.126.63.1                     168.126.63.1                           Ok - o
======================================================================================================================

 - Installed Packages check                                                                                        
======================================================================================================================
 Configuration                       Target                           Current                                Result
======================================================================================================================
 /root/anaconda-ks.cfg               @Base                            Not exist                          Not ok - x
 /root/anaconda-ks.cfg               @Core                            Not exist                          Not ok - x
 /root/anaconda-ks.cfg               @directory-client                Not exist                          Not ok - x
 /root/anaconda-ks.cfg               @hardware-monitoring             Not exist                          Not ok - x
 /root/anaconda-ks.cfg               @korean-support                  @korean-support                        Ok - o
 /root/anaconda-ks.cfg               @large-systems                   Not exist                          Not ok - x
 /root/anaconda-ks.cfg               @network-file-system-client      Not exist                          Not ok - x
 /root/anaconda-ks.cfg               @network-tools                   Not exist                          Not ok - x
 /root/anaconda-ks.cfg               @performance                     Not exist                          Not ok - x
 /root/anaconda-ks.cfg               @perl-runtime                    Not exist                          Not ok - x
 /root/anaconda-ks.cfg               @server-platform                 Not exist                          Not ok - x
 /root/anaconda-ks.cfg               compat-expat1                    Not exist                          Not ok - x
 /root/anaconda-ks.cfg               gcc                              Not exist                          Not ok - x
 /root/anaconda-ks.cfg               python-devel                     Not exist                          Not ok - x
 /root/anaconda-ks.cfg               python-setuptools                Not exist                          Not ok - x
 /root/anaconda-ks.cfg               python-tools                     Not exist                          Not ok - x
 /root/anaconda-ks.cfg               telnet                           Not exist                          Not ok - x
 /root/anaconda-ks.cfg               vim-enhanced                     Not exist                          Not ok - x
======================================================================================================================

 - IPv4 check                                                                                                      
======================================================================================================================
 Configuration                       Target                           Current                                Result
======================================================================================================================
 net.ipv4.ipfrag_time                15                               Not exist                          Not ok - x
 net.ipv4.tcp_max_syn_backlog        8192                             Not exist                          Not ok - x
 net.ipv4.tcp_retries2               7                                Not exist                          Not ok - x
 net.ipv4.tcp_fin_timeout            20                               Not exist                          Not ok - x
 net.ipv4.tcp_keepalive_probes       2                                Not exist                          Not ok - x
 net.ipv4.tcp_keepalive_time         60                               Not exist                          Not ok - x
 net.ipv4.tcp_keepalive_intvl        10                               Not exist                          Not ok - x
======================================================================================================================

```

* You can make a checklist what you want as below
* $] cat /data/var/checklist.txt
```
# List for the system check

# Syntax is [Title],[Target value],[Commandi line for result]

# You can use the variable as below name for include the variables
# $TargetVar_ID,$LineSort_Var2,$LineSort_Var3 

# Also you can add a Line Breaker for the groups by minus character(-) in front of line
#
# List for the system check
#
# # Syntax is [Title],[Target value],[Commandi line for result]
#
# # You can use the variable as below name for include the variables
# # $TargetVar_ID,$LineSort_Var2,$LineSort_Var3 
#
# # Also you can add a Line Breaker for the groups by minus character(-) in
# front of line
# #
#- System Defult check
CentOS Version,6.4,`lsb_release -r | awk '{print $2}'`
Kernel Version,2.6.32-358.el6.x86_64,`uname -r`
Locale,ko_KR.UTF-8,`locale | grep LANG | awk -F '=' '{print $2}'`
Umask,002,`cat /etc/bashrc | grep "umask 0" | tail -1 | awk '{print $2}'`
Ulimit,8192,`ulimit -n`
Selinux,disabled,`cat /etc/selinux/config |grep "^SELINUX=" | awk -F "=" '{print $2}'`
Init,3,`cat /etc/inittab |grep ^id | awk -F ':' '{print $2}'`
Service DIR,applications,`ls / |egrep "^$LineSort_Var2"`
Service account,service,`cat /etc/passwd | grep "service" | awk -F ':' '{print $1}'`
Monitoring account,nagios,`cat /etc/passwd | grep "nagios" | awk -F ':' '{print $1}'`
DNS-1st,8.8.8.8, `cat /etc/resolv.conf | awk  'NR==1 {print $2}'`
DNS-2nd,168.126.63.1, `cat /etc/resolv.conf | awk  'NR==2 {print $2}'`

- Installed Packages check
/root/anaconda-ks.cfg,@Base,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,@Core,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,@directory-client,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,@hardware-monitoring,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,@korean-support,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,@large-systems,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,@network-file-system-client,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,@network-tools,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,@performance,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,@perl-runtime,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,@server-platform,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,compat-expat1,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,gcc,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,python-devel,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,python-setuptools,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,python-tools,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,telnet,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`
/root/anaconda-ks.cfg,vim-enhanced,`sudo cat /root/anaconda-ks.cfg |grep "^$LineSort_Var2$"`

- IPv4 check
net.ipv4.ipfrag_time,15,`cat /etc/sysctl.conf |grep "$TargetVar_ID" | awk '{print $3}'`
net.ipv4.tcp_max_syn_backlog,8192,`cat /etc/sysctl.conf |grep "$TargetVar_ID" | awk '{print $3}'`
net.ipv4.tcp_retries2,7,`cat /etc/sysctl.conf |grep "$TargetVar_ID" | awk '{print $3}'`
net.ipv4.tcp_fin_timeout,20,`cat /etc/sysctl.conf |grep "$TargetVar_ID" | awk '{print $3}'`
net.ipv4.tcp_keepalive_probes,2,`cat /etc/sysctl.conf |grep "$TargetVar_ID" | awk '{print $3}'`
net.ipv4.tcp_keepalive_time,60,`cat /etc/sysctl.conf |grep "$TargetVar_ID" | awk '{print $3}'`
net.ipv4.tcp_keepalive_intvl,10,`cat /etc/sysctl.conf |grep "$TargetVar_ID" | awk '{print $3}'`

```

* Help page
* $] hwconfig -h
```
=====================================================================
 hwconfig <no options> 	for the normal view
 hwconfig -h or --help	for the help page
 hwconfig -r 		for the data refreash
 hwconfig -c 		for create an output data
 hwconfig -net 		for show the network status
=====================================================================
 hwconfig -check	for check the system configration
=====================================================================
 hwconfig -check --file [FILE NAME] 	for use a custome check
=====================================================================
```




[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/goody80/hwconfig/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

