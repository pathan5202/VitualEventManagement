docker pull jasonrivers/nagios
docker run -d --name nagios_monitor -p 8080:80 jasonrivers/nagios

1. Launch an EC2 Instance
Steps:
Go to AWS Console → EC2 → Launch Instance
Select:
AMI: Ubuntu Server 22.04 LTS
Instance Type: t2.micro (Free-tier eligible)
Key Pair: Create/Select key
Security Group Rules:
SSH → Port 22 → My IP
HTTP → Port 80 → Anywhere
Custom App Port (if needed) → e.g., 5000, 3000
Launch instance.

ssh -i yourkey.pem ubuntu@13.233.124.90

sudo apt update -y
sudo apt install docker.io git -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ubuntu   # Allow docker without sudo

exit
ssh -i yourkey.pem ubuntu@13.233.124.90

git clone https://github.com/yourusername/your-repo.git
cd your-repo

FROM node:18
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]

docker build -t myapp .

docker run -d -p 3000:3000 myapp

