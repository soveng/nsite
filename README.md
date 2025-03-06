## Nsite-Upload

This repo is setup to be a small starter for deploying a static site as a Nsite using the Nsite-CLI.
In general this repo is setup to auto deploy using Github action but also can be used with the CLI to deploy from the terminal.

This is build on top of the work of some great folks: [Lez](https://github.com/lez) [flox1an](https://github.com/flox1an) [hzrd149](https://github.com/hzrd149)


## Nsite Deploy Instructions  
**~ 15 min guide**  

## Introduction  
The Nsite setup consists of two components/repositories:  
1. **The Nsite** – Contains the GitHub action deploy script.  
2. **The Nsite Gateway** – Resolves the site through its `npub` and connects the domain.  

---

## Prerequisites  
- GitHub Account  
- `Nsec` in Hex format  
- Domain name *(optional)*  
- Cloudflare or Vercel Account *(GitHub Pages may also work)*  

---

## 1) Nsite Repository  

### 1.1) Clone the Repository  
Go to the [Nsite-Upload GitHub Repo](https://github.com/Nsite-Info/Nsite-Upload) and select **Use this template** to clone it.  

![Clone Repo](https://raw.githubusercontent.com/Nsite-Info/Nsite-Basics/refs/heads/main/images/1.png)

### 1.2) Set Your Nsec Hex as an Action Secret  
1. Navigate to **Settings** in your repo.  
2. Under **Secrets and variables**, select **Actions**.  

![Nav Secrets](https://raw.githubusercontent.com/Nsite-Info/Nsite-Basics/refs/heads/main/images/2.png)

3. Click **Add a New Repository Secret**.  

![Add Secret](https://raw.githubusercontent.com/Nsite-Info/Nsite-Basics/refs/heads/main/images/3.png)

4. Name it: `NSITE_KEY`  Set the secret as your `Nsec` in hex format.  

![Add Name - Hex Key](https://raw.githubusercontent.com/Nsite-Info/Nsite-Basics/refs/heads/main/images/4.png)


### 1.3) Redeploy the Action  
Once the secret is set:  
1. Go to the **Actions** tab in the repo.  

![Actions Menu](https://raw.githubusercontent.com/Nsite-Info/Nsite-Basics/refs/heads/main/images/5.png)

2. Because the deployment failed, click **Re-run jobs** to redeploy with the newly set `Nsec`.  

![Retrigger Action](https://raw.githubusercontent.com/Nsite-Info/Nsite-Basics/refs/heads/main/images/6.png)

![Running Action](https://raw.githubusercontent.com/Nsite-Info/Nsite-Basics/refs/heads/main/images/7.png)

### 1.4) 🎉 Successfully Deployed! 🎉  
After deployment, the `npx` command will show the deployment details, including the live URL on **Nsite.lol Gateway**.  

![Succes Message](https://raw.githubusercontent.com/Nsite-Info/Nsite-Basics/refs/heads/main/images/8.png)

- Any changes made to `index.html` will be deployed automatically when pushed.  

---

### 1.5) FAQ & Debugging  

#### **Q: My Deployment Failed**  
You might not have set any Blossom servers for your **BUD-03 List**.  
1. Visit [Nsite Debug](https://nsite.info/debug), enter your `npub`, and check for missing configurations.  
2. Set your Blossom Server List via [Bouquet](https://bouquet.slidestr.net).  

Alternatively, try deploying locally:  
1. Download the repo to your local machine.  
2. Install [Node.js](https://nodejs.org/en).  
3. Set your `Nsec` in `.nsite/project.json`. *(Modify other settings if needed)*  
4. Run in the terminal from the root directory:  

   ```sh
   npx nsite-cli upload www
   ```  

#### **Q: My Changes Are Not Visible**  
- **Nsite.lol has caching**, so updates may not appear immediately.  
- **Try Nsite.cloud**, which does not have caching and should reflect updates immediately. *(Note: Nsite.cloud only supports simple single-page HTML sites.)*  
- **The Blossom server might not serve the blob via public access.**  

---