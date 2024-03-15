<style scoped>
.main {
  width: 100%;
  min-height: 100vh;
}

.submit-btn {
  transition: all 0.3s ease;
}

.submit-btn:hover {
  transform: scale(1.05);
}

.preview-image {
  width: 80%;
}

.preview-details-body {
  width: 70%;
}

.preview-details {
  position: absolute;
  top: 77%;
  width: 100%;
}

.preview-content {
  height: 77%;
}

.preview {
  background: url("../assets/bgImg.jpg");
  background-size: cover;
  background-position: bottom;
}
@media (max-width: 576px) {
  .form-container {
    background: linear-gradient(to right, #00b09b, #2cf7df);
    border-radius: 10px;
    padding: 20px;
    width: 90%;
    height: auto;
  }
  .preview {
    width: 90%;
    min-width: 529px;
    min-height: 520px;
  }

  .preview-image {
    width: 80%;
  }

  .preview-details-body {
    max-height: 9rem;
    width: 70%;
    min-height: 8rem;
  }

  .preview-details {
    position: absolute;
    top: 71%;
    width: 100%;
  }

  .preview-content {
    height: 77%;
  }
}

@media (min-width: 576px) {
  .form-container {
    background: linear-gradient(to right, #00b09b, #2cf7df);
    border-radius: 10px;
    padding: 20px;
    width: 90%;
    height: auto;
  }
  .preview {
    width: 90%;

    min-height: 480px;
  }

  .preview-image {
    width: 80%;
  }

  .preview-details-body {
    max-height: 9rem;
    width: 70%;
    min-height: 8rem;
  }

  .preview-details {
    position: absolute;
    top: 68%;
    width: 100%;
  }

  .preview-content {
    height: 77%;
  }
}

@media (min-width: 768px) {
  .form-container {
    background: linear-gradient(to right, #00b09b, #2cf7df);
    border-radius: 10px;
    padding: 20px;
    width: 50%;
    max-width: 700px;
    height: auto;
  }
  .preview {
    width: 60%;
    max-width: 700px;
    min-height: 480px;
  }

  .preview-image {
    width: 80%;
  }

  .preview-details-body {
    max-height: 10rem;
    width: 70%;
    min-height: 8rem;
  }

  .preview-details {
    position: absolute;
    top: 61%;
    width: 100%;
  }

  .preview-content {
    height: 77%;
  }
}

@media (min-width: 992px) {
  .preview {
    min-height: 520px;
  }
  .preview-image {
    width: 80%;
  }

  .preview-details-body {
    max-height: 8rem;
    width: 70%;
    min-height: 8rem;
  }

  .preview-details {
    position: absolute;
    top: 77%;
    width: 100%;
  }

  .preview-content {
    height: 77%;
  }
}

@media (min-width: 1200px) {
  .preview {
    min-height: 590px;
    max-width: 660px;
  }
  .preview-image {
    width: 80%;
  }

  .preview-details-body {
    width: 70%;
    min-height: 8rem;
    max-height: 9rem;
  }

  .preview-details {
    position: absolute;
    top: 78%;
    width: 100%;
  }

  .preview-content {
    height: 77%;
  }
}
</style>

<template>
  <div class="main">
    <div class="main2 py-3">
      <div v-auto-animate class="container">
        <div class="w-100 d-flex justify-content-center">
          <div id="app" class="mt-5 form-container shadow-lg">
            <div class="row">
              <div class="col-md-6 offset-md-3">
                <h2 class="mb-4">Generate Post</h2>
                <form @submit.prevent="handleSubmit" enctype="multipart/form-data" class="">
                  <div class="mb-3">
                    <label for="image" class="form-label fw-semibold">Image</label>
                    <input type="file" class="form-control" id="image" @change="handleImageChange" />
                  </div>
                  <div class="mb-3">
                    <label for="details" class="form-label fw-semibold">Details</label>
                    <textarea class="form-control" placeholder="Enter Details" id="floatingTextarea" v-model="formData.details"></textarea>
                  </div>
                  <div class="mb-3">
                    <label for="details" class="form-label fw-semibold">Tag</label>
                    <input class="form-control text-capitalize" placeholder="Sports/News/Politics/Notice" id="floatingTextarea" v-model="formData.tag" />
                  </div>
                  <!--  <div class="mb-3">
                    <label for="details" class="form-label fw-semibold">Select Day</label>
                    <select id="exampleFormControlInputBudget" class="form-select" v-model="formData.day">
                      <option class="bg-light text-secondary" value="0">Monday</option>
                      <option class="bg-light text-dark" :value="item.value" v-for="item in days" :key="item">{{ item.day }}</option>
                    </select>
                  </div> -->
                  <div class="">
                    <button type="submit" class="btn btn-primary submit-btn">Submit</button>
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
        <!-- ///////////////////////////////////////////////////////////////////////////////////////////////////////////// -->
        <div v-auto-animate v-if="submited" class="preview-area w-100 mt-5">
          <div class="preview-container w-100 d-flex justify-content-center">
            <div class="preview py-3 position-relative">
              <div class="position-relative preview-content">
                <div class="preview-body mt-1 d-flex justify-content-center">
                  <div class="preview-image">
                    <div v-auto-animate class="w-100 h-100 p-2 bg-light">
                      <div v-auto-animate class="w-100 h-100 bg-light position-relative">
                        <img :src="formData.image" class="border-0 w-100 h-100" alt="..." />
                        <div class="position-absolute top-0 end-0 mt-2 me-2">
                          <img src="../assets/CircularLogo_gn_noBg.png" class="img-thumbnail bg-transparent border-0 opacity-75 float-end" alt="..." style="width: 20%; height: auto" />
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div v-auto-animate class="preview-details text-dark d-flex justify-content-center">
                  <div class="preview-details-body bg-light rounded py-2 px-2">
                    <!-- Set min-height -->
                    <div class="h-100 position-relative">
                      <div class="d-flex justify-content-center" style="height: 100%">
                        <img src="../assets/CircularLogo_gn_noBg.png" class="img-thumbnail bg-transparent border-0 opacity-50" alt="..." style="width: auto; height: 100%" />
                      </div>
                      <div class="h-100 w-100 position-absolute start-0 top-0 preview-details-body-content">
                        <div class="d-flex justify-content-between preview-details-body-content-header mb-1">
                          <span class="bg-danger px-2 rounded text-light fw-semibold text-capitalize">{{ formData.tag }}</span>
                          <span class="fw-semibold text-primary" style="text-decoration: underline">{{ formData.day }},{{ formData.date }}</span>
                        </div>
                        <div class="d-flex preview-details-body-content-body justify-content-center px-2" style="height: calc(100% - 25px)">
                          <span class="d-flex align-items-center" style="height: 100%">
                            <span>
                              <h5 class="fw-bold" style="text-align: left">{{ formData.details }}</h5>
                            </span>
                          </span>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="preview-footer my-1 text-light mb-3 position-absolute bottom-0 w-100">
                <div class="d-flex justify-content-evenly">
                  <img src="../assets/CircularLogo_gn.png " class="img-thumbnail mx-2" alt="..." style="width: 50px; height: 50px" />

                  <img src="../assets/Footerbanner.png" class="img-thumbnail bg-transparent border-0 mx-2" alt="..." style="height: 50px" />
                </div>
              </div>
            </div>
          </div>
          <div class="d-flex justify-content-center mt-3">
            <button @click="downloadPreview" class="btn btn-primary submit-btn">Download Preview</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { toast } from "vue3-toastify";
import "vue3-toastify/dist/index.css";
import html2canvas from "html2canvas";

export default {
  name: "PostGeneratore",

  data() {
    return {
      days: [
        { day: "Monday", value: "Mon" },
        { day: "Tueday", value: "Tue" },
        { day: "Wednesday", value: "Wed" },
        { day: "Thursday", value: "Thu" },
        { day: "Friday", value: "Fri" },
        { day: "Saturday", value: "Sat" },
        { day: "Sunday", value: "Sun" },
      ],
      submited: false,
      formData: {
        details: "",
        image: null,
        tag: "",
        date: "",
        day: "0",
      },
    };
  },
  methods: {
    handleImageChange(event) {
      const file = event.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = (e) => {
          this.formData.image = e.target.result;
        };
        reader.readAsDataURL(file);
      }
    },
    handleSubmit() {
      console.log("handleSubmit Called");
      if (this.formData.details == "") {
        toast.error(`Enter Details`, {
          autoClose: 1500,
        });
        return;
      }

      if (this.formData.image == null) {
        toast.error(`Select Image`, {
          autoClose: 1500,
        });
        return;
      }
      if (this.formData.tag == "") {
        toast.error(`Enter Tag`, {
          autoClose: 1500,
        });
        return;
      }

      /*  if (this.formData.day == "0") {
        toast.error(`Select Day`, {
          autoClose: 1500,
        });
        return;
      } */

      let daysOfWeek = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
      let currentDate = new Date();
      let currentDay = daysOfWeek[currentDate.getDay()];
      this.formData.day = currentDay;

      let currentDate2 = new Date();
      let formattedDate = currentDate2.toLocaleDateString(); // Format the date as needed
      this.formData.date = formattedDate;

      this.submited = true;
      // You can perform form submission logic here
      console.log("Form submitted:", this.formData);
      // Example: Send form data to the server using axios or fetch API
    },

    downloadPreview() {
      console.log("downloadPreview Called");

      // Select the preview area
      const preview = document.querySelector(".preview");

      // Use html2canvas to capture the preview area
      html2canvas(preview).then((canvas) => {
        // Convert canvas to data URL
        const dataURL = canvas.toDataURL("image/png");

        // Create a link element
        const link = document.createElement("a");
        // Set link attributes
        link.href = dataURL;
        link.download = "preview.png";
        // Simulate click on the link to trigger download
        link.click();
      });

      console.log("downloadPreview Ended");
    },
  },
};
</script>
