# Nmap-practice
i started learning cybersecurity and one of the first things i explored was how to find devices on a network and scan them using Nmap.This repo documents everything I learned from finding IP adresses all the way to detecting vulnerabilities on a network.i have not gone deep into exploiting yet but i understand what is running and why it matters.
##What is Nmap?
Nmap(network mapper) is a free open source tool used to scan networks.It helps you discover devices ,find open ports,detect what services are running and even find potential vulnerabilities.It is widely used in cybersecurity for reconnaissance.
##step 1-finding your IP
You need to know your own ip adress before scanning,on linux type this command on your terminal:
ip a
Your local ip will look something like 192.168.1.X meaning you are on private home network.
##step 2-scanning for network devices
You can now scan entire network to see every connected device to it,this is called a ping sweep it checks who is active on network without scanning ports:
nmap -sn 192.168.1.0/24
##step 3-Finding your router
your router is usually the first device on the network ending in .1,this command shows you open ports on your router and confirm its the route way of your network:
nmap 192.168.1.1
##step 4-scanning for open ports
ports are like doors on a device,each port runs a diffrent service.scanning ports tells you what doors are open:
#scan the most common 1000 ports
nmap 192.168.1.1
#scan a specific range of ports
nmap -p 1-1000 192.168.1.1
#scan all 65535 ports
nmap -p- 192.168.1.1
###common ports to know:
port 80-HTTP(website)
port 443-HTTPS(secure website)
port 22-SSH(remote access)
port 21-FTP(file transfer)
port 3389-RDP(remote desktop)
##step 5-detecting what is running on those ports 
finding what services and version is running on open ports,this is useful because you can then look up if that version has known  vulnerabilities:
nmap -sV 192.168.1.1
##step 6-agressive scan(get everthing at once)
The -A flag runs OS dtection,version detection,script scanning and traceroute all at once:
nmap -A 192.168.1.1
##step 7-finding vulnerabilities
Nmap has a scripting engine called Nmap Scripting Engine(NSE) that can check for known vulnerabilities on services,does not exploit anything just checks if vulnerabilities exist and reports them:
#run all defaults scripts
nmap -sC 192.168.1.1
#scan specifically for vulnerabilities
nmap --script vuln 192.168.1.1
#combine version detection with scripts
nmap -sV -sC 192.168.1.1
##step 8-scan everything together
This is most complete scan-all ports,all info,vulneraility check.It takes longer but gives you full picture:
nmap -A -p- --script vuln 192.168.1.1
###What I Have Learned So Far
-How to find own ip adress and understand network
-How to discover all devices connected to a network
-How to find open ports on any device
-How to detect what services and versions are running
-How to identify my router and what it exposes
-How to use Nmap scripts to check for vulnerabilities
-The diffrence between a quiet scan and an aggresive scan
###













