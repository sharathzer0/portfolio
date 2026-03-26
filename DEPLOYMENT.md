# Google Cloud Deployment Guide for Portfolio

This guide explains how to host your static portfolio website (`index.html`, `styles.css`, `script.js`, and assets) on Google Cloud Storage for free or very low cost.

## Prerequisites
1. A Google Account.
2. An active Google Cloud Platform (GCP) account (you get $300 free credit when you sign up).
3. The Google Cloud Console accessible via browser.

## Step 1: Create a Google Cloud Storage Bucket
1. Open the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project (e.g., `sharath-portfolio`).
3. Navigation menu > **Cloud Storage** > **Buckets**.
4. Click **Create** to create a new bucket.
   - **Name your bucket**: Ensure it's globally unique (e.g., `sharath-network-portfolio`). If using a custom domain, name the bucket exactly as your domain (e.g., `www.yourdomain.com`).
   - **Location type**: Choose a Region close to your audience (e.g., `asia-south1` for Mumbai).
   - **Storage class**: Choose **Standard**.
   - **Access control**: Choose **Uniform** to easily apply permissions to all files.
   - **Protection tools**: Uncheck Object Versioning to save costs.
5. Click **Create**.

## Step 2: Make the Bucket Public
To allow anyone on the internet to view your portfolio:
1. In the Cloud Storage Buckets list, click on your bucket's name.
2. Go to the **Permissions** tab.
3. Click **Grant Access** (or **Add Principal**).
4. Under *New principals*, type `allUsers`.
5. Under *Select a role*, choose **Cloud Storage** > **Storage Object Viewer**.
6. Click **Save** and confirm to allow public access.

## Step 3: Upload Your Files
1. Go to the **Objects** tab in your bucket.
2. Click **Upload Files**.
3. Select *every* file from your portfolio directory (`index.html`, `styles.css`, `script.js`, and `sharath_resume.pdf`).
4. Wait for the upload to complete.

## Step 4: Configure the Bucket as a Website
1. Go back to the **Buckets** list.
2. Find your bucket, click the three-dot menu (⋮) on the far right, and select **Edit website configuration**.
3. In the **Main page (index) suffix** field, type `index.html`.
4. In the **404 (Not Found) page** field, you can also type `index.html` (or a custom 404 page if you create one).
5. Click **Save**.

## Step 5: View Your Website
Your website is now live! The URL format is:
`https://storage.googleapis.com/[YOUR_BUCKET_NAME]/index.html`

(For example: `https://storage.googleapis.com/sharath-network-portfolio/index.html`)

## Optional: Custom Domain Mapping (HTTPS)
If you purchase a custom domain (e.g., `sharathkumar.net`), you can connect it:
1. Instead of linking from the bucket directly, you should use **Firebase Hosting** or **Google Cloud Load Balancer** with Cloud Storage to automatically handle free SSL (HTTPS) certificates and edge caching. 
2. FireBase Hosting is highly recommended for static portfolios as it comes with a generous free tier.
   - Install Firebase CLI (`npm install -g firebase-tools`).
   - Run `firebase login` and `firebase init`.
   - Choose `Hosting`, point the public directory to your portfolio folder.
   - Run `firebase deploy`.

Congratulations on launching your modern Network Engineer portfolio!
